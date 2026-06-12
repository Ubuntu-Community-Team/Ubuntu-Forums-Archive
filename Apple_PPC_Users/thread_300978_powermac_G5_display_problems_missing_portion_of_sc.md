---
title: "powermac G5 display problems missing portion of screen"
date: 2006-11-16
forum: Apple PPC Users
---

### Post by keyword_eddie on 2006-11-16
Hi, new to ubuntu (and linux in general) can't fix this problem
Fresh install of ubuntu edgy on powermac G5 (PowerMac11,2):

[IMG]http://i85.photobucket.com/albums/k79/eddiegarside/edgyproblem2.jpg[/IMG]

Tried new kernel, nvidia gfx driver and ubuntu updates
If I change resolution the black bar stays the same size, when i updated the drivers there were no extra resolutions to try and the custom res had no effect. My card is geforce 6600LE, tried different monitors which didn't change anything :-k 
If i print-screen i get the whole screen saved.

Has anyone had similar problems or any suggestions? ta.

---

### Post by dpny on 2006-11-16
Have you tried editing your xorg.conf file?

---

### Post by stream303 on 2006-11-17
Have you tried running:
[B]
sudo dpkg-reconfigure -fgnome -phigh xserver-xorg[/B]

choosing nv and then setting the native resolution of your monitor?

It doesn't work for everyone from what I've heard.

---

### Post by keyword_eddie on 2006-11-22
:mrgreen: :mrgreen: :mrgreen: :mrgreen: :mrgreen: 

the "sudo dpkg-reconfigure -fgnome -phigh xserver-xorg" worked perfect.

Cheers stream303 ;)

---

### Post by stream303 on 2006-11-22
Great!  I liked the screenshot btw.

Is that an lcd monitor?  If so, you may want to eek the last bit of performance out of the standard nv driver with the "FPDither"  "true" option in your xorg.conf:

[http://www.ubuntuforums.org/showthread.php?t=303366](http://www.ubuntuforums.org/showthread.php?t=303366)

It worked great for me on my 20" iMac screen.

---

