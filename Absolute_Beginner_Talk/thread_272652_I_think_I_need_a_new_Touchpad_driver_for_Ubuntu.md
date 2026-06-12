---
title: "I think I need a new Touchpad driver for Ubuntu"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by Shiny Fork on 2006-10-06
When I first got the laptop, a Dell Latitude c600, I had trouble with the touchpad moving on its own erractically, and fixed it by installing a driver for XP from [www.synaptics.com](www.synaptics.com)
However, I just installed Ubuntu for the first time, and am having the same trouble. The cause was originally from having both the pointing stick and pad enabled; disabling the stick from the driver fixed it. Is there a way to do the same in Ubuntu, or a place where I can get a driver to fix it?

---

### Post by Rob_Frohne on 2006-10-09
I don't have a solution for you, but I think I have the same problem.  Sometimes I can't click, and the only thing I can do to get back control of clicking on the mouse is to do a ctrl-alt-F1 and then an alt-f7 to come back to the gui.

Rob

---

### Post by bodhi.zazen on 2006-10-09
LOL :lol:

Try tpconfig and/or ksynaptics:
```
sudo aptitude install tpconfig
```
```
sudo aptitude install ksynaptics
```
If that fails: 

[Disable touchpad](http://scottcollins.net/blog/2006/01/disable-touchpad-tap-in-kubuntubreezy.html)

---

