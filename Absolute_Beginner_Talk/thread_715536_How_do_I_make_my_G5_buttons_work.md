---
title: "How do I make my G5 buttons work?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by infernohit on 2008-03-04
My back and forward buttons don't work. Instead, the forward button acts the same as right-clicking and the back button acts the same as "Paste".

---

### Post by hoges on 2008-03-05
I know for the G15 keyboard there's a whole range of addons for the macro keys. I assume it's the same for the G5 mouse.

Found [this link ]("http://adterrasperaspera.com/blog/2006/06/20/logitech-g5-review-under-linux")through google. Looks promising.

---

### Post by infernohit on 2008-03-05
Thanks for the link.

How do I edit my /etc/X11/xorg.conf's InputDevice section? I don't even know how to open it. >.>

---

### Post by Fred_E _krugar on 2008-03-05
sudo gedit /etc/X11/xorg.conf

---

### Post by Fred_E _krugar on 2008-03-05
Hang on a tick and I will give you my settings so all you have to do is cut and paste.

---

### Post by Fred_E _krugar on 2008-03-05
Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "auto"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7 4 5 6

---

### Post by infernohit on 2008-03-05
I pasted that and pressed save. I'll try rebooting to see if it works.

---

### Post by infernohit on 2008-03-05
Thanks, those buttons are working now.

Does your wheel work? I'm not talking about the tilting because I don't know what that's for, but I mean when you press down on the wheel to scroll.

---

### Post by archmage258 on 2008-03-05
you should make a backup of your file before you make any changes to it.  I thought I had but didn't and I caused my graphics card to no longer be recognized (really weird) and ended up having to.reinstall. :(

---

### Post by Fred_E _krugar on 2008-03-05
I havent figured that out yet sorry.

---

### Post by infernohit on 2008-03-05
> **archmage258 said:**
> you should make a backup of your file before you make any changes to it.  I thought I had but didn't and I caused my graphics card to no longer be recognized (really weird) and ended up having to.reinstall. :(

Too late for that. >_>

---

### Post by Plasma_NZ on 2008-03-22
Has anyone got this to work under Hardy Heron yet..? im stumped and i refuse to use btnx - far too complex.. when in 7.04 and 7.10 the fix was simple... seem's too drastic.. am slowly pulling my hair-out not being able to use tilt wheels as back/forward on my Logitech G5 .. help help ! haha

---

### Post by infernohit on 2008-03-24
It was actually working for me under hardy heron but now for some reason, it stopped working.

---

