---
title: "Massive Problem/Error"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Native Dialect on 2007-03-24
I recently switched back to my old CRT Proview monitor, from my old Sony SDM M51 Flat Panel LCD monitor. It happens to support a higher resolution (1280x1024). When I booted Ubuntu (I dual boot with Windows XP...thank God), I notced that it didn't recognize the additional resolution, so I entered the terminal and put in this line 

sudo dpkg-reconfigure xserver-xorg

I didn't change anything until I got to the area about selecting my resolution. I used Space Bar to select the appropriate new resolution (1280x1024) and I hit Ctl+Alt+Backspace to save the settings. When I restarted the system, I got an error message about the X Server and now I can't log into Ubuntu at all. I figured that it was no dirt off my shoulder...i'd just reinstall Ubuntu (I am using Edgy Eft) and I could just try again and learn what to do better. But now, I can't even reinstall Ubuntu from the Live CD, because I get the same X Server error message. What do i do? My slave drive is now totally useless because it can't boot Ubuntu and Windows no longer recognizes is at a slave drive. Please help me. I would like to continue to use Ubuntu...and I understand that it will require patience...but this is the kind of encounter than can sour grapes (so to speak). So any help would be greatly appreciated.

---

### Post by Native Dialect on 2007-03-24
Somebody please help...

---

### Post by lamalex on 2007-03-24
you could try downloading/installing the alternate cd. that's my guess

---

### Post by freebird54 on 2007-03-24
You could find out what the dpkg-reconfigure renamed your xorg.conf file backup to, and recopy it over the current one.  I don't suppose there's any chance you noted the name it gave you when done? :)

Basically, choose the recovery console then:

```
ls /etc/X11
```

notice the names of files like xorg.conf and similar - such as **xorg.conf.20070316075924**  (which I think means it backed it up on Mar 16 2007 at 0759 hrs)  so copy it over the xorg.conf and retry...

```
cp etc/X11/xorg.conf.20070324xxxxxxxxx /etc/X11/xorg.conf
```

replacing the numbers and xxx's above with your values.  Should get you in for a retry!

---

### Post by Native Dialect on 2007-03-24
while I didn't directly use your suggestion Freebird, it did lead to a solution. I looked over all of my xorg configuration information and discovered that some how, switching monitors reverted my settings to my onboard graphics card. So I merely had to reinstall my Nvidia drivers, to correct the problem. So thank you very much.

---

### Post by freebird54 on 2007-03-25
The best solutions are the ones you find yourself..... someone said that!

Glad you got it, and that I was at least getting you to look in the right place :)

---

