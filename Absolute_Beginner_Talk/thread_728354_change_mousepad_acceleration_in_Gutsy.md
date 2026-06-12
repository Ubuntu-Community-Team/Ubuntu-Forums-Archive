---
title: "change mousepad acceleration in Gutsy?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by holdie on 2008-03-18
I'm trying to get the acceleration for my mousepad on my laptop to work, but it doesn't seem to matter what I change it to, nothing changes...

If I use a USB mouse, then it works perfectly, so it would appear there is some disconnect between the program and the mousepad...that being said, anyone know how to work around this?

thanks

---

### Post by amazingtaters on 2008-03-18
Try installing GSynaptics. It works wonderfully for me and gives me easy, gui based control over my touchpad.

---

### Post by holdie on 2008-03-18
i've got gsynaptics installed...when I used it to edit the mouse buttons or simply deactivate the touchpad it works perfectly, but when I try and edit the sensitivity and acceleration with it there isn't any difference...

is this something i need to edit in xorg or something?

---

### Post by amazingtaters on 2008-03-18
Hmm that's odd. Let me ratle this one around in my head (and via google-fu) for a while.

Well, this thread may help.
[http://ubuntuforums.org/showthread.php?t=134242](http://ubuntuforums.org/showthread.php?t=134242)

---

### Post by holdie on 2008-03-18
so I went ahead and edited my xorg file, adding the AccelFactor option and playing around with the values...that seemed to work pretty well, just a pain in the *** since I have to restart xorg each time I want to see how it works...thanks a bunch for the link though

---

