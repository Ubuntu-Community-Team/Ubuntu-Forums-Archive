---
title: "How do I run epsxe in ubuntu"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-23
Coz everytime I try to run .img files to it. It just closes, is it in conflict w/ xgl?
I tried downloading & extracting the file but the folders don't seem to show up. I'm really confuse & its hard for me to explain what happen bcoz it nver seemed to happend in windows!

---

### Post by kris2pe on 2006-07-23
OK I found a guide 
[http://terror.snm-hgkz.ch/gaming/linux/epsxe_howto/](http://terror.snm-hgkz.ch/gaming/linux/epsxe_howto/)
Can anyone pls help me!!!
I'm @ step 9 

We're getting close to a working PSX emulator now! Unfortunately, there seem to be a few problems when using multithreading, which is apparently required for certain GPU and/or SPU plug-ins. ePSXe (or the plug-in) seems unable to locate libpthread, which is necessary for this. That's why you should locate the file "libpthread.so.0" (might be "libpthread-0.9.so" or some such name) on your system and copy it to your ePSXe directory. Then you'll need to apply this workaround, and the one in step 10:

cp /lib/libpthread.so.0 $EPSXE/

I don't understand it coz I place $EPSXE to another directory which ~/epsxe/
should I transfer those files here?

---

### Post by kris2pe on 2006-07-23
can u guys recommend another guide 4 this coz I really @ lost w/ all mumbo jumbo here. 
In windows not that I'm repeating but this would have been much much easier!
Pls help serious! Do not ignore!!!

---

### Post by Saphira on 2006-07-23
Have you tried here?

[http://doc.gwos.org/index.php/Playstation_Emulator](http://doc.gwos.org/index.php/Playstation_Emulator)

---

### Post by kris2pe on 2006-07-23
Already done that! It works but I don't hear any sound!! 
Is there away for me to install another plugin for video & sound. 
Coz I really don't know how to add other plugins! 
My video card is ATI 9800 & my sound card is a Creative Live.
Are there plugins that work more efficiently than what was instructed?

---

### Post by michaeljb2005 on 2006-08-01
> **kris2pe said:**
> Already done that! It works but I don't hear any sound!! 
Is there away for me to install another plugin for video & sound. 
Coz I really don't know how to add other plugins! 
My video card is ATI 9800 & my sound card is a Creative Live.
Are there plugins that work more efficiently than what was instructed?

ePSXe does conflict with xgl if you are rendering it using opengl.  In order to get it to even start you are going to have to use the nonXgl hack and even then it will be a little slower than normal especially if you are using high end settings.  So if your card is barely handling it now it will be slower.

---

