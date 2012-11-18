jQuery Knob
=============

- canvas based ; no png or jpg sprites.
- touch, mouse and mousewheel, keyboard events implemented.
- downward compatible ; overloads an input element.
- nice ticks for various styling effects
- shadow effect for the knob
- gradients

Example
-------

```html
    <input type="text" value="75" class="dial">

    <script>
    $(function() {
        $(".dial").knob();
    }
    </script>
```

Options
-------

Options are provided as attributes 'data-option':

```html
    <input type="text" class="dial" data-min="-50" data-max="50">
```

... or in the "knob()" call :

```javascript
    $(".dial").knob({
                    'min':-50
                    ,'max':50
                    })
```

The following options are supported :

Behaviors :
* min : min value | default=0.
* max : max value | default=100.
* angleOffset : starting angle in degrees | default=0.
* angleArc : arc size in degrees | default=360.
* stopper : stop at min & max on keydown/mousewheel | default=true.
* readOnly : disable input and events | default=false.

UI :
* cursor : display mode "cursor" | default=gauge.
* thickness : gauge thickness.
* width : dial width.
* height : dial height | default=[same as width].
* displayInput : default=true | false=hide input.
* displayPrevious : default=false | true=displays the previous value with transparency.
* fgColor : foreground color | default=#87CEEB
* bgColor : background color | default=#EEEEEE
* canvasBgColor : background color for the knob | default=false

UI - ticks ( _new_ ) :
* ticks : displays ticks or not | default=false.
* tickLength : length of the ticks, consistent with the thickness of the gauge (if equal, the ticks take the full thickness of the gauge) | default=80% of thickness
* tickWidth : width of the ticks | default=0.02
* tickColor : Default tick color | default=#CCCCCC
* tickFgColor : Default foreground tick color | default=#0088CC

UI - shadow ( _new_ ) :
* shadow : amount of blur of the shadow effet | default=0 (no shadow at all)
* shadowColor : color of the shadow | default=rgba(0,0,0,0.5)

Gradients
-------

To make the foreground color a gradient, just pass an array of colors and color stops as the fgColor parameter as per below :

```html
    <script>
    $(".dial").knob({
                        'fgColor' : ['0', '#5FAAC1', '0.5', '#0000FF', '1', '#FFFFFF']
                    });
    </script>
```

> NB : Adding a gradient can only be done programmatically.

As it is a linear gradient form, it works well with half-circles dials.

Hooks
-------

```html
    <script>
    $(".dial").knob({
                        'release' : function (v) { /*make something*/ }
                    });
    </script>
```

* 'release' : executed on release

    Parameters :
    + value : int, current value

* 'change' : executed at each change of the value

    Parameters :
    + value : int, current value

* 'draw' : when drawing the canvas

    Context :
    - this.g : canvas context 2D (see Canvas documentation)
    - this.$ : jQuery wrapped element
    - this.o : options
    - this.i : input
    - ... console.log(this);

* 'cancel' : triggered on [esc] keydown

The scope (this) of each hook function is the current Knob instance (refer to the demo code).

Example
-------

```html
    <input type="text" value="75" class="dial">

    <script>
    $(".dial").knob({
                     'change' : function (v) { console.log(v); }
                    });
    </script>
```

Dynamically configure
-------

```html
    <script>
    $('.dial')
        .trigger(
            'configure',
            {
            "min":10,
            "max":40,
            "fgColor":"#FF0000",
            "skin":"tron",
            "cursor":true
            }
        );
    </script>
```

Set the value
-------

```html
    <script>
    $('.dial')
        .val(27)
        .trigger('change');
    </script>
```

Supported browser
-------

Tested on Chrome, Safari, Firefox, IE 9.0.


Credits
-------

Forked from aterrien (https://github.com/aterrien/jQuery-Knob - http://anthonyterrien.com/knob/)

Thanks to eskimoblood (https://github.com/eskimoblood/jQuery-Knob)