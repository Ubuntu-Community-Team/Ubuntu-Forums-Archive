---
title: "shadows in gtk themes"
date: 2008-10-04
forum: Art &amp; Design
---

### Post by elefantcrossing on 2008-10-04
just wanted to know if it is possible to get drop shadows in gtk themes? 
I've made a quick mockup to illustrate my question

---

### Post by jonian_g on 2008-10-04
Only if you use a compositing manager like compiz or enable compositing for metacity.

---

### Post by oedipuss on 2008-10-05
I suppose you can fake some of the effects with a pixmap engine, though.
If I'm not mistaken there are already themes that have a thin shadow inside textboxes or lists.

---

### Post by xreaper on 2008-10-05
theres always a way to do things on linux! if you have compiz enabled, type:

sudo apt-get install compizconfig-backend-gconf

then go to System>preferences>advanced desktop effects settings. find the button that says Window Decoration, and click on it, you can then play around with the opacity, color, etc of the shadow. Enjoy ^^

---

### Post by oedipuss on 2008-10-05
I think he means composited drop shadows in gtk widgets, like the nautilus icon area in the mockup.

---

### Post by elefantcrossing on 2008-10-05
yes, i wasn't talking about the shadows of the window decorations. 
i wanted to know if there is any gtk theme that uses composited shadows for gtk widgets. as seen on my mockup. 

since the murrine-engine will have nice alpha transparency, i thought composited shadows would be the next evolutionary step.

---

### Post by smartboyathome on 2008-10-05
> **elefantcrossing said:**
> yes, i wasn't talking about the shadows of the window decorations. 
i wanted to know if there is any gtk theme that uses composited shadows for gtk widgets. as seen on my mockup. 

since the murrine-engine will have nice alpha transparency, i thought composited shadows would be the next evolutionary step.

The only ways to do it are to use a theming engine which supports it (I don't know if any do), or to use pixmaps.

Murrine's no longer under development, by the way. Cimi had to even leave the Art team mailing list. So it won't happen there unless someone forks it or something.

---

### Post by Ub1476 on 2008-10-05
I thought murrine-svn supported it?

---

