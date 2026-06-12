---
title: "Ubuntu Inkscape problems"
date: 2007-06-08
forum: Art &amp; Design
---

### Post by izak on 2007-06-08
Hi all

Ok, I've got a very strange Inkscape bug, so I'm going to describe it in some detail:

I've created a graph in python using matplotlib and saved it as an svg. However, when I open it in inkscape only the axes of the graph are displayed and not the data. But, when I ungroup everything, I can see the bounding boxes of the datapoints. However, I can't see the ellipses that make up of the datapoints (it's as if they have no fill). I can select one, try to fill it, shift it to the front, make sure the opacity is set, but it remains stubbornly invisible.

Now here's the weird part: If I open the same file with the windows version of Inkscape, everything is visible as it should be. Also if I export the file to EPS (using Ubuntu inkscape) the graph becomes visible again.

Can anyone help me? Please! Or is this just a bug :(

---

### Post by durand on 2007-06-08
What colour are the axis?

---

### Post by izak on 2007-06-11
Everything is supposed to be black. It is black in the original plot and black when I open it with the windows inkscape.

---

### Post by ZERO_SHIFT on 2007-06-11
Did you post it on launchpad?

and do you know any good documentation for INkscae that I can use ?

Thanks

---

### Post by izak on 2007-06-11
I posted it on the sourceforge inkscape mailing lists. What's launchpad?

Nope sorry, I don't use inkscape extensively, basically it's just a way to enable me to edit my matplotlib plots slightly (correct spelling mistakes etc.).

---

### Post by durand on 2007-06-11
you can use launchpad to post any bugs you have. It's quite neat and more people will look at what you post. Here's the inkscape page: [https://launchpad.net/Inkscape](https://launchpad.net/Inkscape) .You will need to register though.

---

