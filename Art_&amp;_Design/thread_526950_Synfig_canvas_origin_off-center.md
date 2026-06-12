---
title: "Synfig canvas origin off-center?"
date: 2007-08-16
forum: Art &amp; Design
---

### Post by kickabear on 2007-08-16
Okay, this one is driving me crazy.  I found Synfig after a long search for a 2D animation program.  I'm really excited about it.  It looks like it will do exactly what I want, with room for me to grow.  It's cool.

However, when I attempt to follow the tutorial, I get as far as "draw a circle" and I run into a problem.  When I click on the canvas with the circle tool, the program displays a piece of a circle, as if I'm drawing a huge circle about 3 feet in diameter.  The canvas is only big enough to show a small arc from this circle.  Also, when I release the mouse button, the circle arc disappears from the canvas.  The circle does appear in the layer list, but no part of it is visible on the canvas.  

This same problem exists for all tools, such as rectangle, bline, etc. 

Any thoughts?  Thanks!

---

### Post by kickabear on 2007-08-16
Here is a jpeg showing the problem.  I've drawn a circle.  The center is set to some random spot far off the canvas, and the radius is zero.  If I manually set the center to 0,0 and the radius to a positive integer, I can see a circle on the canvas.  

The random center seems to be different with each execution of Synfig Studio. 

Thanks!

---

### Post by Dooglus on 2007-10-11
This was a known problem.

[http://wiki.synfig.com/FAQ#I.27m_using_synfigstudio_on_a_laptop_but_can.27t_draw_anything_using_my_mouse._What_gives.3F](http://wiki.synfig.com/FAQ#I.27m_using_synfigstudio_on_a_laptop_but_can.27t_draw_anything_using_my_mouse._What_gives.3F)

The bug doesn't happen in synfig 0.61.06 and newer.

For any other bug reports, please use the synfig bug tracker:
[http://sourceforge.net/tracker/?group_id=144022&atid=757416](http://sourceforge.net/tracker/?group_id=144022&atid=757416)

---

