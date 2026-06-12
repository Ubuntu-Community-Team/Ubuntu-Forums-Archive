---
title: "SVG rendering problem (Firefox)"
date: 2009-03-05
forum: Art &amp; Design
---

### Post by dreamincode on 2009-03-05
Hi,

I haven't done much programming in SVG before. I'm hoping an expert can help me out with this problem.

I have a piece of SVG code that is supposed to render crosshairs at specific x,y coordinates on a page. 

The code works fine when the SVG width and height attributes are the same values as the width and height of the SVG viewbox.

Example, this works:
<svg id="explodedHead" x="0" y="0" width="500px" height="500px" viewBox="0 0 500 500">

See: 
[http://207.45.186.206/_TMP/SVG/example.php](http://207.45.186.206/_TMP/SVG/example.php)
[http://207.45.186.206/_TMP/SVG/example.svg](http://207.45.186.206/_TMP/SVG/example.svg)


The code does NOT WORK when I make the SVG width and height attributes smaller than the SVG viewbox values. 

Example, this doesn't work:
<svg id="explodedHead" x="0" y="0" width="250px" height="250px" viewBox="0 0 500 500">


See: 
[http://207.45.186.206/_TMP/SVG/example2.php](http://207.45.186.206/_TMP/SVG/example2.php)
[http://207.45.186.206/_TMP/SVG/example2.svg](http://207.45.186.206/_TMP/SVG/example2.svg)

Can anyone explain what I am doing wrong? Shouldn't this simply shrink the SVG canvas? I don't understand why this should effect the display of the crosshairs.

Thanks,

---

### Post by smartboyathome on 2009-03-05
You might try using Inkscape to see what the problem is. :)

---

