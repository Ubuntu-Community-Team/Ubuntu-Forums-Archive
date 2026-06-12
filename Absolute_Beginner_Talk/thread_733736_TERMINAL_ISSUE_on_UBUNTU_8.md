---
title: "TERMINAL ISSUE on UBUNTU 8"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by kumags2 on 2008-03-24
newbie 'ir on linux....I recently installed ubuntu 6 yesterday and upgrade it to ubuntu 8 just this morning.... after the installation and the reboot. i just figure that the title bar on my mozilla does not show and as I go to the terminal window it only shows white screen and cannot type anything into it....

I tried other options such as pressing ctrl +alt+ f1... but no response at all.... I hope you could have a quick reply on this one... co'z I wud really like to learn linux commands..:confused:

---

### Post by kpkeerthi on 2008-03-24
Can you post the output of ```
cat /etc/X11/xorg.conf
``` ?

** Please use [code] tags

---

### Post by bhavi on 2008-03-24
Bump! Compiz problem I think... Hardy is still a development version of ubuntu.. What are your system specs?

---

### Post by Jimmyfj on 2008-03-24
Seems that your upgrade has gone wrong in some way.

If you have the possibility to do so, go to [www.ubuntu.com](www.ubuntu.com) and get the iso for a complete 8.04 disk and make a clean install from that.

---

### Post by kumags2 on 2008-03-24
I can't put anything on the terminal window.... are there still any chances to fix this, other than reinstalling the version 8... or should I say I'll just install the version 7.10 instead...

---

### Post by bhavi on 2008-03-24
> **Jimmyfj said:**
> Seems that your upgrade has gone wrong in some way.

If you have the possibility to do so, go to [www.ubuntu.com](www.ubuntu.com) and get the iso for a complete 8.04 disk and make a clean install from that.

Yes +1 from me too..

---

### Post by kpkeerthi on 2008-03-24
It could be a simple color depth issue. Boot into Recovery Mode from GRUB. At the command prompt type ```
cat /etc/X11/xorg.conf | grep -i defaultdepth
``` and post back the result. Worth a try before you reinstall the whole thing.

---

### Post by kpkeerthi on 2008-03-24
To save a copy of xorg.conf, boot into Recovery Mode console and type
```
cat /etc/X11/xorg.conf > /home/<your-user-id>/xorg.conf.backup
```

Now boot normally and open xorg.conf.backup in your favorite editor and post the content here.

**Or**

(In normal mode)
Press ALT + F2, type **nautilus** <enter>, press <CTRL> + L. In the location bar, navigate to /etc/X11. Look for xorg.conf. Open with a text edit and post the content.

---

