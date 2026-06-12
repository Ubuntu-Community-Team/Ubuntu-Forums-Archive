---
title: "Inkscape - canvas &amp; resize"
date: 2013-02-23
forum: Art &amp; Design
---

### Post by Perfect Storm on 2013-02-23
Hello,


Is there an easy way in Inkscape to change canvas and making the image to scale with it?
Like I'm building a 128x128 .svg icon but want to make it a 64 .svg afterwards.


regards
A.I.

---

### Post by MG&amp;TL on 2013-02-23
The way I'd do it (probably not optimal, but it works): 

1) Edit the canvas size (Ctrl-Shift-D, then use the dialog).

2) Select all of your work on the icon, group it, scale it using the "W" and "H" measurements on the top bar, then ungroup it.

Although why you're doing this is a little bit of a mystery to me. The whole point of SVG is that it scales regardless of resolution?

---

### Post by Perfect Storm on 2013-02-23
> **MG&TL said:**
> The way I'd do it (probably not optimal, but it works): 

1) Edit the canvas size (Ctrl-Shift-D, then use the dialog).

2) Select all of your work on the icon, group it, scale it using the "W" and "H" measurements on the top bar, then ungroup it.

Although why you're doing this is a little bit of a mystery to me. The whole point of SVG is that it scales regardless of resolution?

Thanks.

I'm just following the Humanity schema. They have their .svg files resized.

---

### Post by prokoudine on 2013-02-23
> **Artificial Intelligence said:**
> 
Is there an easy way in Inkscape to change canvas and making the image to scale with it?
Like I'm building a 128x128 .svg icon but want to make it a 64 .svg afterwards.

You wouldn't want to do that in the first place, unless you want a crappy looking icon :)

You don't automatically get pixel grid alignment when you scale an SVG down. You really need to adjust it manually for each size. Check out one-canvas workflow:

[http://blogs.gnome.org/patrys/2008/07/14/improved-one-canvas-workflow/](http://blogs.gnome.org/patrys/2008/07/14/improved-one-canvas-workflow/)

---

### Post by Perfect Storm on 2013-02-23
> **prokoudine said:**
> You wouldn't want to do that in the first place, unless you want a crappy looking icon :)

You don't automatically get pixel grid alignment when you scale an SVG down. You really need to adjust it manually for each size. Check out one-canvas workflow:

[http://blogs.gnome.org/patrys/2008/07/14/improved-one-canvas-workflow/](http://blogs.gnome.org/patrys/2008/07/14/improved-one-canvas-workflow/)

Thanks, I'll check it out.

---

### Post by alexfish on 2013-02-25
don' know if this type of embedded will help ,

but worth experimenting with  , change the values of the first line 

```
<svg width='300' height='300'>

    <svg width='100%' height='100%'>

    <rect x='0' y='0'  width='100%' height='30' rx='0' ry='0' fill='blue' stroke='black' stroke-width='1'/>

    </svg>
</svg>
```

Added / sort of viewport /clipping 

```
<svg width='100' height='300'>

    <svg width='100%' height='10' x='0' y='40'>

    <rect x='0' y='0'  width='100%' height='30' rx='0' ry='0' fill='blue' stroke='black' stroke-width='1'/>

        </svg>
</svg>
```

BR
Alex

---

### Post by alexfish on 2013-03-07
Though about doing an update on this , 

here  the intitial design is done with Inkscape.

but then need to use scripting to get the desired effects

```
    <svg id='Radio buttons' x='0' y='0' width='75' height='120' >

    <defs>
    <linearGradient id='brown_button_off' gradientUnits='objectBoundingBox'  x1='1' x2='1' y1='0' y2='1'> 
        <stop stop-color='#EFEFEF' offset='.1'/> <stop stop-color='brown' offset='1'/>
    </linearGradient>
    </defs>

    <defs>
    <pattern id='radio_group' width='75' height='30'  patternUnits='userSpaceOnUse'>
        <rect x='2' y='2'  rx='3' ry='3' width='71' height='26' fill='url(#brown_button_off)' stroke='black' stroke-width='1'/> 
        <circle cx='12' cy='15'  r='5' fill='#FFFFFF' stroke='red' stroke-width='3'/>
    </pattern>
    </defs>

        <rect x='0' y='0' width='100%' height='100%'
            ry='0' fill='white' fill-opacity='1' stroke='black'  stroke-width='1' style='display:1 ' />
        <desc>vertical radio group </desc>
        <svg id='radio_group_1' x='0' y='0' width='100%' height='100%'>
            <rect id='radio_group_1' fill='url(#radio_group)' sencex='100' stroke='black' stroke-width='1' width='100%' height='100%'/>
            <sensitive x='0' y='0' width='300' height='300'/>
            <circle cx='12' cy='15'  r='4' fill='#000000'/>
            <text x="0" y="0" dx='20' dy='20' fill="black" >Radio 99</text>
            <text x="0" y="0" dx='20' dy='50' fill="black" >Radio 2</text>
            <text x="0" y="0" dx='20' dy='80' fill="black" >Radio 3</text>
            <text x="0" y="0" dx='20' dy='110' fill="black" >Radio 4</text>
        </svg>
    </svg>
```

can start by changing the values in first row in multiples of the initial value IE:
```
    <svg id='Radio buttons' x='0' y='0' width='150' height='120' >

    <defs>
    <linearGradient id='brown_button_off' gradientUnits='objectBoundingBox'  x1='1' x2='1' y1='0' y2='1'> 
        <stop stop-color='#EFEFEF' offset='.1'/> <stop stop-color='brown' offset='1'/>
    </linearGradient>
    </defs>

    <defs>
    <pattern id='radio_group' width='75' height='30'  patternUnits='userSpaceOnUse'>
         <rect x='2' y='2'  rx='3' ry='3' width='71' height='26'  fill='url(#brown_button_off)' stroke='black' stroke-width='1'/> 
        <circle cx='12' cy='15'  r='5' fill='#FFFFFF' stroke='red' stroke-width='3'/>
    </pattern>
    </defs>

        <rect x='0' y='0' width='100%' height='100%'
            ry='0' fill='white' fill-opacity='1' stroke='black'  stroke-width='1' style='display:1 ' />
        <desc>vertical radio group </desc>
        <svg id='radio_group_1' x='0' y='0' width='100%' height='100%'>
             <rect id='radio_group_1' fill='url(#radio_group)'  sencex='100' stroke='black' stroke-width='1' width='100%'  height='100%'/>
            <sensitive x='0' y='0' width='300' height='300'/>
            <circle cx='12' cy='15'  r='4' fill='#000000'/>
            <text x="0" y="0" dx='20' dy='20' fill="black" >Radio 99</text>
            <text x="0" y="0" dx='20' dy='50' fill="black" >Radio 2</text>
            <text x="0" y="0" dx='20' dy='80' fill="black" >Radio 3</text>
            <text x="0" y="0" dx='20' dy='110' fill="black" >Radio 4</text>
        </svg>
    </svg>
```

Have fun

Alex

---

### Post by blackdoor90 on 2013-03-14
Thanks, sharing such problem and it's solution. I was needed this help.
Thanks again.

---

### Post by amdev on 2013-03-15
> **prokoudine said:**
> You wouldn't want to do that in the first place, unless you want a crappy looking icon :)

You don't automatically get pixel grid alignment when you scale an SVG down. You really need to adjust it manually for each size. Check out one-canvas workflow:

[http://blogs.gnome.org/patrys/2008/07/14/improved-one-canvas-workflow/](http://blogs.gnome.org/patrys/2008/07/14/improved-one-canvas-workflow/)
This reply help me!!!

---

### Post by alexfish on 2013-03-27
**using xlink:**

You can be in control using the  xlink: . very simple to use , can almost show almost any image + scale is automatic if main is set to 100% , all that is
needed is to set width and height.

Things to do set the path to the image / have left my original file path in code to help , but sure U will get it to work

```
<svg width="100%" height="100%" >

    <desc> Change the  xlink:href="file:///path to IE: this example = 'file:///home/alexfish/Desktop/svg-demo.png'  </desc>
    <desc> Change the  width= + height=  </desc>
    <desc> Result = Size auto  </desc>
    <image
       xlink:href="file:///home/alexfish/Desktop/svg-demo.png"
       x="0"
       y="0"
       width="50"
       height="50"
     />
</svg>
```

Have fun

Alex

---

