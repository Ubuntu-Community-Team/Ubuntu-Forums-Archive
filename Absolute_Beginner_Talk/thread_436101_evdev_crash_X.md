---
title: "evdev crash X"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by codedmin on 2007-05-07
Hi there, i have one logitech G7 mouse i see some post so i can have it work in my feisty, however all the posts need evdev driver in mouse section but when i put evdev driver in my xorg the X don't start.

Any info how to solve the problem???

Thanks

---

### Post by codedmin on 2007-05-07
need this please...

---

### Post by rhussong on 2007-05-20
I had the same problem after an edgy->feisty upgrade.  I was using event5 for my Logitech mouse, but feisty creates event5 itself (I don't know why).  I noticed that /dev/input/event2 did not exist, so I switched to event2 in two places:
  - in /etc/udev/rules.d/19-local.rules (your filename may be different), I mapped the Logitech mouse to event2
  - in /etc/X11/xorg.conf, I set the "Device" option of "InputDevice" to "/dev/input/event2".

I used event2, rather than event9 or something, because I saw that a lot of people have their mouse on event2, so I thought it might be magic for Ubuntu.  In any case, it now works.

I also had to change my .Xmodmap, because I previously had switched buttons 2 and 3, and now they automatically come out right.  So, instead of "pointer = 1 3 2 4 5 8 9 6 7 10 11 12", it now says "pointer = 1 2 3 4 5 8 9 6 7 10 11 12".

---

### Post by codedmin on 2007-06-04
Hy, that really work out.

Now my X don't crash. But i can't get my side button to work yet.

How do you do that? Thanks

---

