---
title: "wacom help--screensize problem"
date: 2007-06-04
forum: Art &amp; Design
---

### Post by 4KvRMU7Nnv on 2007-06-04
Ok, the wacom DOES work, but the problem is that I think it doesn't know the size of my screen correctly.  Normally, when the pen is at one corner of the tablet, the cursor is at that corner of the screen.  However, this is not the case.  Does anyone know how to change this?

EDIT:: nevermind, I found the answer.  Simply add the following into the /etc/X11/xorg.conf file under the Inputdevice "cursor" section

Option  "Mode"    "relative"

also, to enable pressure sensitivity, under the stylus section

Option "PressCurve" "50,0,100,50"

I am happy now!

---

