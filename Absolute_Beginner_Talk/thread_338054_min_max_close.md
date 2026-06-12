---
title: "min max close"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-01-13
How do I put the min max close buttons on the left side of the window bar?

---

### Post by aysiu on 2007-01-13
Use KDE or IceWM?

**Edit**: Or follow this tutorial:
[http://www.codejacked.com/move-your-maximize-minimize-and-close-buttons-to-the-left-side-of-the-window/](http://www.codejacked.com/move-your-maximize-minimize-and-close-buttons-to-the-left-side-of-the-window/)

---

### Post by ComplexNumber on 2007-01-13
> **kbsuperstar said:**
> How do I put the min max close buttons on the left side of the window bar?
unfortunately, there isn't a straightforward way of doing this. for most themes, you will have to edit the metacity-theme-1.xml file in the metacity-1 directory for any particular theme you want to edit.

---

### Post by kbsuperstar on 2007-01-13
I use Gnome

---

### Post by kbsuperstar on 2007-01-13
How do I edit that metacity file?

---

### Post by aysiu on 2007-01-13
> **kbsuperstar said:**
> How do I edit that metacity file?
Visit the link I posted. It explains everything.

---

### Post by ComplexNumber on 2007-01-13
> **aysiu said:**
> Use KDE or IceWM?

**Edit**: Or follow this tutorial:
[http://www.codejacked.com/move-your-maximize-minimize-and-close-buttons-to-the-left-side-of-the-window/](http://www.codejacked.com/move-your-maximize-minimize-and-close-buttons-to-the-left-side-of-the-window/)

nice one, aysiu :). it works too! i've just changed "menu: minimize,maximize,close" to "minimize,maximize,close:menu"
i didn't know that, but i should have known to look in gconf-editor. i just didn't think it would be there.

---

### Post by aysiu on 2007-01-13
> **ComplexNumber said:**
> nice one, aysiu :). it works too! i've just changed "menu: minimize,maximize,close:menu" to "minimize,maximize,close:menu"
i didn't know that, but i should have known to look in gconf-editor. i just didn't think it would be there.
I was amazed at how quickly I could come up with it using a simple Google search. And the tutorial has screenshots, too!

---

### Post by ComplexNumber on 2007-01-13
> **aysiu said:**
> I was amazed at how quickly I could come up with it using a simple Google search. And the tutorial has screenshots, too!
there really is lots of useful shortcuts and things that one can find when using gconf-editor. i always have it on my panel so that i can get to it easily.

---

