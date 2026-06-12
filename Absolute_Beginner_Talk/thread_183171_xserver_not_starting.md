---
title: "xserver not starting"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by knewmocker on 2006-05-27
Every time I try to startx i get the error that it can not start. it says to look at the 
/var/log/Xorg.0.log. I use cat and when I do it all gose by real quick on my screen and I cant fix it. 

I do have ATI and everyone says to do sudo dpkg-reconfigure xserver-xorg
and type vesa. But I also never see where I should put vesa in at all. Im a total noob so I need alot of help

---

### Post by AndyCooll on 2006-05-27
It might be an idea to use "cat" with the "less" command. That way it will only scroll down a few lines at a time, giving you plenty of time to read.

However, when going through the reconfigure process, read every bit carefully. The bit you want is where it is asking about your video card. Since you have an ati the install process will probably know this and have already highlighted "ati" for you, don't accept it. You don't actually have to type in "vesa" anywhere, it is one of the choices available in the list, scroll through them until it appears.

:cool:

---

### Post by knewmocker on 2006-05-27
wow thank you so much I would have never guessed that was where I had to have vesa

---

