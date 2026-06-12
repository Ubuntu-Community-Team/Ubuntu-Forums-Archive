---
title: "eye of gnome couldn't scroll"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-10-24
i couldn't use my scroll wheel to zoom in and out image after upgrade to 7.10. this function worked well in 7.04 . please help

---

### Post by bortx on 2007-10-24
I've noticed the same problem, it was a very usefull issue to zoom in and out with mouse track ball, but in 7.10 this function is dissabled. I thin it is a back step. 

Anyone knows how to modify this?

---

### Post by Hospadar on 2007-10-24
what program is this?

---

### Post by bortx on 2007-10-24
ubuntu's default image viewer

---

### Post by afeasfaerw23231233 on 2007-10-24
it should be ''eog'' i think. when i download image from the net to my desktop, i double-click it and this viewer appears

---

### Post by JackS on 2007-10-24
I had been using v5.10 for the past two years.  Eye Of Gnome recognizes the middle mouse button and scroll wheel.  I can
pan & zoom with it.

Last Friday I installed v7.10 and everything went very smoothly.
Initial testing revealed the same problem you have found.  When
using the middle mouse button/wheel in EOG, nothing happens!

I found a workaround for this.  Before you use the mmb/wheel,
press and hold the CTRL key first.  Then the mmb/wheel will work
like it did in previous versions of EOG.

Why did the developers introduce this new "feature"?  Don't know.

-Jack

---

### Post by afeasfaerw23231233 on 2007-10-24
in the ''preference'' i cannot find anything about my mouse scroll wheel. so nothing can be changed

---

### Post by JackS on 2007-10-25
I am using a PS2  mechanical 3-button mouse + scroll wheel.  Looks alot like a Logitech.

In eog v2.13.2, the left mouse button does the panning, the middle button/wheel scrolls &zooms.

In eog v2.20.0, the left mouse button does nothing and the middle button also does nothing.
Hold down the Ctrl key while pressing the mouse keys and it works as in version 2.13.2!

(This may be a bug, or I have been living in a cavern for two years and need retraining.)
I thought I would give ubuntu v7.10 a test-drive.  :-)


If your mmb/wheel does not work with other applications, try troubleshooting your mouse
driver.  If your mmb/wheel works ok elsewhere, use both hands in eog. <shrug>
-Jack

---

### Post by gbutalid on 2007-10-25
I think they're trying to standardize ZOOMING in GNOME applications. Using **Ctrl**+**+** you can "zoom in" in nautilus, evince, eog. This is also default in Firefox and Flock - though they are not GNOME apps. It also follows that **F11** is for fullscreen, except in OpenOffice, which irritates me. This is not a step back for EOG.

---

### Post by afeasfaerw23231233 on 2007-10-25
but i want zooming works by just scrolling the wheel

---

### Post by Handssolow on 2007-10-28
> **afeasfaerw23231233 said:**
> but i want zooming works by just scrolling the wheel
me too
I looked in Gnome's Help file and zoom is now CTRL + scroll wheel with Gutsy,  a step backwards I think.
I didn't find any option in Properties where this can be changed back to how things were in Feisty where the scroll wheel is active in Gnome without having to hold down CTRL.

Is there a solution?

---

### Post by plueken on 2007-10-30
There is a setting in gconf called scroll_wheel_zoom, and if I set that, at least the scroll wheel functionality works again, in order to zoom in and out.  But it still doesn't allow me to pan with the left mouse button, so it's still an incomplete fix for the old functionality.

---

### Post by Handssolow on 2007-10-31
Many thanks plueken, I've got my scroll wheel working without having to press CTRL at the same time. Using  gconf-editor took me a while to find Apps>eog>view as I was looking in the Gnome area, anyway all's well that ends well.

---

### Post by afeasfaerw23231233 on 2007-11-01
n00b ... how to do that gconf called scroll_wheel_zoom

---

