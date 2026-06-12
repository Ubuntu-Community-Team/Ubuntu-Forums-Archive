---
title: "restore video card confg."
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by kgys on 2008-03-26
i have installed ubuntu 7.10 last week, and i  activated 3d cube.its working fine.:guitar:

by seeing a video in youtube that window get fireup by closing in beryl.

to get that effect i tried to do the steps posted  in a website, as part of it they instructed to add three line in xorg.conf file in device list. after restart by alt+ctrl+backspace. error shows you are running in low graphiccard, and my resolution changed to 800*600, no 3d cube effect.
when i gone to screen resolution option there it shows only max of 800*600.
i also tried to restore the cofiguration file, but it didnt work.

help me.:confused:

---

### Post by kesman on 2008-03-26
What graphics card do you have? To enable more functions in compiz, you need to install ccsm from synaptic.
To reconfigure your graphics, use
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by kpkeerthi on 2008-03-26
I suggest you do this from 'Recovery Mode' from GRUB menu. Boot into recovery mode and at the command prompt type
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and choose the driver and supported resolutions. Reboot.

To get the Visual Effects, see [http://www.thelinuxnewbie.com/2007/10/21/running-desktop-visual-effects-on-gutsy-gibbon-ubuntu-710/](http://www.thelinuxnewbie.com/2007/10/21/running-desktop-visual-effects-on-gutsy-gibbon-ubuntu-710/)

---

### Post by oedha on 2008-03-26
Cancelled !!

---

### Post by kesman on 2008-03-26
> **oedha said:**
> Cancelled !!

wut?

---

### Post by madara_sama on 2008-03-26
The simple way you have to do is, you just need to remove your graphic card driver, and don't forget to disabled your desktop effect if you use it. Then reinstall it again.

---

### Post by oedha on 2008-03-26
> **kesman said:**
> wut?

Please read my edit message Dear kesman :lolflag:

---

### Post by kesman on 2008-03-26
Oh, silly me :F

---

