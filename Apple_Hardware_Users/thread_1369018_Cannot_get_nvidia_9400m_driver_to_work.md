---
title: "Cannot get nvidia 9400m driver to work"
date: 2009-12-31
forum: Apple Hardware Users
---

### Post by cm-jp1 on 2009-12-31
Hey everyone
Im new to these forums and to ubuntu. Yes i have searched.
I currently have a late 2008 intel mac unibody and recently install ubuntu 9.10 successfully through bootcamp. I searched and searched trying to find a way to enable the visual effects but had no luck. The different ways ive tried was to look for it in the hardware manager with no luck and also installed it on OS X then opened terminal and tried sh nvidia-64_185 but no luck with that either. ( i didnt type that exactly, but im at work and dont have the exact code infront of me)
 
This is prob a noob question and prob has been reviewed before, but i cannot find it.
 
Any Info or links to a How TO would be great. 
 
Thanks Alot
 
-Chase

---

### Post by cm-jp1 on 2010-01-01
No one knows anything about this ?

---

### Post by epz on 2010-01-01
2 things.
  Are you able at least to open a shell? (I mean without slows or graphic getting you mad)

   Do you know how to install nvidia drivers? 

   I suppose you are using 32 bit version of ubuntu.
   I don't really know how things work on bootcamp (despite I'm a mac user) but I have to assume that being a 'not-aggressive' partitioning utility you are in a native enviroment.

     Then go here [http://www.nvidia.com/object/linux_display_ia32_190.53.html](http://www.nvidia.com/object/linux_display_ia32_190.53.html)

  Download your drivers and then follow this guide.
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

 As far as I know (at least when I had to do it, it worked in that way) you can skip directly to 'prepare configuration files' but if you prefer to avoid any risk follow the whole guide.

---

