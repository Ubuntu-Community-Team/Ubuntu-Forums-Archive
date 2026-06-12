---
title: "start up video mode not supported"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Aane on 2007-07-16
I have been running live ubuntu 7.04 on a Dell Dimension 4700 with a dell lcd monitor and ati radeon x300 video card.  As ubuntu loads, the screen goes black and a message displays - video mode not supported.  However, after about 10 seconds, ubuntu continues to load and eventually starts up - at a display resolution of 1024 x 768, which is the same resolution I run Win XP.

My question is - what does this error message mean?  (Somewhere I remember someone posting a comment that this is something peculiar to Dell monitors.)  I would like to know if this message is significant as I have not experienced many other issues running live ubuntu on this system so far (I connected to the internet, saw videos on You tube, printed Open Office docs on my printer, edited some photos - all typical things I do on this home computer).

Thanks in advance for any advice or assistance with my question.

Aane

---

### Post by jordanmthomas on 2007-07-16
Does it display this on the vurtual terminals or in X?
Chances are, your virtual terminals need the resolution fixed.

Try this:  edit /boot/grub/menu.lst 
```

kernel /boot/vmlinuz26 root=/dev/sda1 ro vga=869 

```
find the first line similar to this ^^  (the first line starting with kernel)
if you don't have anything that says vga=xxx then add this:
```
vga=792
``` (or change whatever you have to that)
[http://www.mepis.org/node/2992](http://www.mepis.org/node/2992) 
if it still doesn't work, read here and choose a number that your monitor will support.

---

### Post by Aane on 2007-07-16
The message "video mode supported" displays as live ubuntu loads from the cd.  However, after a few seconds of black screen, the installation does proceed and ubuntu finishes loading and I have been trying it out.  I am just curious about why the message appears.  Thanks.

Aane

---

### Post by jordanmthomas on 2007-07-16
Ahh, you're booting off the LiveCD?  When you first boot, before you hit enter on start or install ubuntu, look for the resolution option.  Try to turn it down some.  Chances are your monitor doesn't support 1024x768 framebuffer (the old-school looking terminals use the framebuffer)  but does for graphical stuff.

Sorry if that didn't make any sense at all...I'm not so great at explaining things sometimes.  :)

---

### Post by Aane on 2007-07-17
I will try your suggestion the next time I run a live session of Ubuntu.  Thank you for the advice.

Aane

---

