---
title: "Keep losing Ubuntu using EXT3 in Windows"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-11
I am having problems with Ubuntu crashing. I am using Windows XP with EXT3 to change the xorg files. However, once I change some input lines and test Ubuntu and return to Windows XP I find that I no longer can open my Ubuntu drive. I am asked if I want to format it. I had formatted it earlier before and during Ubuntu install. Any suggestions on what causes me to lose access to the EXT3 driver that has Ubuntu?

---

### Post by seshomaru samma on 2007-02-12
what changes are you making and why?
you probably need to use the live Cd to reverse those changes so you can log into Ubuntu

---

### Post by kittyhawk63 on 2007-02-12
I can reboot back into Ubuntu after the screen freezes. I am using EXT3 on the advise of others to change the video resolutions. There is a pop up telling me to lower my resolution. I tried this and am working on other input lines in xorg to see if that will help stop the crashes.

---

### Post by seshomaru samma on 2007-02-12
please try to run
```
dpkg-reconfigure xserver-xorg
```
to change your resolution

---

### Post by mr.v. on 2007-02-12
first of all...forget the windows EXT3...if you can boot into ubuntu but simply can't get into the graphical X screen, you can still use the terminals.

Press Ctrl+Alt+F1 to get to a terminal. From there you can use the program nano or vim to edit /etc/X11/xorg.conf

that way you can simply type **startx** after editing the config file to see if your X server will startup without having to reboot each time using a weird windows EXT3 driver...

---

### Post by kittyhawk63 on 2007-02-12
> **mr.v. said:**
> first of all...forget the windows EXT3...if you can boot into ubuntu but simply can't get into the graphical X screen, you can still use the terminals.

Press Ctrl+Alt+F1 to get to a terminal. From there you can use the program nano or vim to edit /etc/X11/xorg.conf

that way you can simply type **startx** after editing the config file to see if your X server will startup without having to reboot each time using a weird windows EXT3 driver...

Thanks. I will take your advise.

---

### Post by skyhopper88 on 2007-02-12
It asked you to reformat in Windows bacause the drives were'nt unmounted correctly on shutdown. You can restart via the commandline then go back in to windows to edit files if need be.

---

### Post by k1001001 on 2007-02-12
> **seshomaru samma said:**
> please try to run
```
dpkg-reconfigure xserver-xorg
```
to change your resolution
Please try this first before editing the xorg.conf.

---

