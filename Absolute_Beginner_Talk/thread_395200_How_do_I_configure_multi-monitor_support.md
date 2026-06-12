---
title: "How do I configure multi-monitor support?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by KillerHamster on 2007-03-27
Finally have the NVIDIA settings working, now I want to run my dual-head 6800 Ultra in clone mode so I can occasionally use my LCD for longer periods as my CRT is at a funny angle). How?? I am so lost on this.

---

### Post by martinw89 on 2007-03-27
Hi!
Good to see that you got your nvidia all worked out, graphics can be tricky in Linux.  I would do this:[LIST=1]
[*]Press Alt+<F2>
[*]Type "gksudo nvidia-settings" (without quotes)[/LIST]NVIDIA's control panel, I believe, has plenty of tools to set up monitors.  But, beware as always, NVIDIA is not the best with Linux drivers (relative to their Windows drivers).  Before you do this, I would **make a copy of your xorg.conf file**, this is important any time we want to change display settings (or anything else in xorg.conf).  To backup your xorg.conf:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```If you ever need to restore the backup (AKA X crashes at startup) do the following:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```I hope this works for you :)

---

### Post by KillerHamster on 2007-03-28
I did backup Xorg.conf just in case anything I do from now on goes wrong, however nvidia-settings does NOT allow for the addition of a second monitor. It only has the options to modify my current monitor (it calls CRT-0), without any option such as nView or any kind of clone modes. I also added the nvidia-settings to my applications menu by creating the file (shown in another thread - neat trick I must say).

How do I go about adding the second monitor? Once I can get a way for X Server to know I have two monitors it shouldn't be too much of an issue (I can configure Xorg now that I know what the hell I am doing).

---

### Post by lamalex on 2007-03-28
might want to try looking here [http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

---

### Post by KillerHamster on 2007-03-28
I seem to have taken 2 steps backwards trying to configure this (wow they make it hard enough dont they?). I had to reinstall the nvidia drivers (somehow it uninstalled them when I added stuff to xorg.conf..), and the backup of xorg.conf worked...but the drivers uninstalled themselves...I really dont get it. I got them working again, but really, how do you enter the "TwinView" into the xorg.conf without blowing it up like I did?

---

### Post by KillerHamster on 2007-03-28
Tried two times so far and have had to use backups twice. I am 0 for 2 now :/

Anyone actually got a clone setup working?

---

