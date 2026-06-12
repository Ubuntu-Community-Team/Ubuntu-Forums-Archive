---
title: "x freezes."
date: 2005-08-19
forum: Absolute Beginner Talk
---

### Post by LunarEagle on 2005-08-19
I installed ubuntu 5.04 (AMD64) today and it boots to the login screen but after I login or even if I try to chose a sertain session than it freezes. Ubuntu works fine in text mode. I am guessing it is my graphics card. I have a Ati radeon express 200M 128mb. I am using a HP Compaq R4000 laptop.

---

### Post by ltracy on 2005-08-19
If you hit ctrl-alt-f1 as soon as you see the round cursor, you can get to console mode.  From there edit your /etc/X11/xorg.conf file by adding 
<b>Option "noaccel"</b> 
immediatly after the line containing <b>Driver   "ati"</b>



Keep checking the forums, and you will find a lot of how-tos and helpful instructions on installing different distros on this laptop.  I, myself, just finished the installation.  Ubuntu is one of the more difficult distros to get working, it requires several modifications.  I am pretty much a brand new newb and was able to follow some of the kernel modifications.  The fglrx driver and xorg.conf files still appear to be giving me some trouble (looking at a 1024x768 mess right now).

---

