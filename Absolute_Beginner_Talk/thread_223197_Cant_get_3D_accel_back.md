---
title: "Cant get 3D accel back?"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by rene100 on 2006-07-26
I've been trying to get my 3D acceleration working with the fglrx drivers.  The last time i did this it killed my 3d.  This time I was careful to backup my xorg.conf file, but now that I lost all 3d acceleration, when I restored my xorg,conf file, I still don't have 3d acceleration?

Am I missing a step?

---

### Post by professor_chaos on 2006-07-26
when you restored, did you restart X? You need to have X reload the xorg.conf file, which it will do with a restart. ```
ctrl+alt+backspace
``` If you end up with out a gui, just a terminal, just login and type ```
sudo /etc/init.d/gdm start
```

---

### Post by rene100 on 2006-07-26
I have my gui and i did ctr-alt-backspace to reboot it, it's just the 3d acceleration that isn't working.  I was trying to upgrade from the 3d accel that came with the install of dapper.  I get 500 fps in glxgears with those drivers, and I'm sure that my video card can do better (mobility radeon 9000)

Anyways, if someone could please let me know how to restore the drivers that came on install (without reinstalling dapper) I would really appreciate the help

---

### Post by codejunkie on 2006-07-26
> **rene100 said:**
> I have my gui and i did ctr-alt-backspace to reboot it, it's just the 3d acceleration that isn't working.  I was trying to upgrade from the 3d accel that came with the install of dapper.  I get 500 fps in glxgears with those drivers, and I'm sure that my video card can do better (mobility radeon 9000)

Anyways, if someone could please let me know how to restore the drivers that came on install (without reinstalling dapper) I would really appreciate the help
not 100% sure on this since i don't have an ati card, but i read that installing the ati and nvidia drivers replaces parts of mesa. i know that this is true on nvidia cards, if you remove the nvidia-glx driver you loose 3d function with the open source nv driver, and reinstalling mesa fixes it so it might work on the ati cards also.
run 
```
sudo apt-get install --reinstall libgl1-mesa libgl1-mesa-dri mesa-utils

```in a terminal to reinstall mesa and restart the xserver and see if this helps.

---

### Post by philippe_carlo on 2006-07-26
The fglrx drivers probably don't work because ATI messed up at some point. You need to overwrite /usr/lib/libGL.so.1.2 with the original version, and you should have 1238.105 FPS or so.

---

### Post by matc on 2006-07-26
What do you mean by original version? If you know some way to get the cards properly working, please provide more information.
(Radeon 9000 here)

---

### Post by philippe_carlo on 2006-07-26
I have a mobility radeon too. I have to copy the attached file in /usr/lib.Make sure to unzip it first.

---

### Post by rene100 on 2006-07-26
where do I find the original file?

---

### Post by rene100 on 2006-07-26
oh, nevermind, you attached it ;) hehehe

---

### Post by rene100 on 2006-07-26
No luck :(  I guess i will try to revert to mesa 3d

---

### Post by rene100 on 2006-07-26
I reverted back to my original xorg.conf and libGL.so.1.2 and then reinstalled the mesa drivers, and I still down have direct rendering (glxinfo) and glxgears is 150 fps :(

---

