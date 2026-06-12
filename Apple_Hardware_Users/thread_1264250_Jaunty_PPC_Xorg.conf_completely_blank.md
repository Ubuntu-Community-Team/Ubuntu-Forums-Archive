---
title: "Jaunty PPC Xorg.conf completely blank?"
date: 2009-09-12
forum: Apple Hardware Users
---

### Post by Exodist on 2009-09-12
OK, I am completely stumped on this. I have 9.04 installed and running on my eMac. It has a Radeon7500 "RV200" and some 3D seems to work, but the screen has a blue tent to it when trying out with such things as GLXGears. That being said I was going to tweak my xorg.conf, but the dang thing is completely blank. I dont much keep up with every change to xorg anymore, but am I missing something here? xorg.conf on my main box is full of information. But on my eMac its as empty as you can get, the file is there but no information has been added.

Anyone have any insight on this?

Thanks,
Exo

---

### Post by cptfx on 2009-09-12
I can't help you with your problem but hopefully I can get you pointed in the ?right? direction.  Now, I'm not 100% sure if my terminology is correct, so don't take this as writ.  But, I believe that Jaunty has discontinued the use of Xorg.conf and uses HAL.  This is true for hardware, but I'm I don't have any monitor related info in /etc/hal.

On my Jaunty ppc there is currently nothing in the  /etc/X11/xorg.conf file.. but I've done abunch of other stuff to my system that seems to have erased it.  It works fine though.  On a fresh install it was present, but got erased/moved at some point.

You may want to look at the man page for xorg.  The -bgamma may be what you're looking for.  If nothing else there is a list of the other locations for config files:
       /etc/X11/xorg.conf 
       /etc/X11/xorg.conf-4
       /etc/xorg.conf 
       /usr/etc/xorg.conf
       /usr/lib/X11/xorg.conf

---

### Post by argosreality on 2009-09-12
Looks like its a bug specifically related to PPC releases [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-r128/+bug/398204](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-r128/+bug/398204) though that but report is now oudated and has been replaced by two seperate ones depending upon your video chipset

---

### Post by sweetleaf on 2009-09-13
The xorg implementation in Jaunty does not require a full xorg.conf file, so it's blank by default. However, it still reads from the file (at /etc/X11/xorg.conf), and settings listed there will take precedence over xorg's internal settings. So, you can add any settings there you might need to fix your problem. 

In addition to the man page for xorg, have a look at the entry for xorg.conf. It can also be helpful to read the Xorg log file at /var/log/Xorg.0.log.

---

### Post by gwydionwaters on 2009-09-16
mine is also blank, 8.10 on ppc powerbookg4, i tried to create one with reconfigure xserver utility and well... that is a bad idea lol i was stuck in low graphics mode and somehow escaped... i just want two finger scrolling

---

