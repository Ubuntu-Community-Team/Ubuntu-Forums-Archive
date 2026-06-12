---
title: "Eject etc on PowerBook"
date: 2004-11-30
forum: Apple PPC Users
---

### Post by Felix_the_Mac on 2004-11-30
I have a fresh install of Ubuntu 4.10 on my PowerBook G4 Aluminium.

First of all I want to say how smooth the install was, everything worked perfectly!!
Much better than YDL 4.0,

Anyway, I have found from the forums that pbbuttonsd is installed by default.
I have checked and it IS running.
However, the volume brightness & eject keys are not working.

I read that I should install powerprefs using Synaptic.
However PowerPrefs does not appear in the list of available packages.

Please can you give advice as to how I should proceed.
Thanks.

---

### Post by slux on 2004-11-30
You'll find powerprefs from the universe repository. just add this to your /etc/apt/sources.list:

```
deb http://archive.ubuntu.com/ubuntu/ warty universe
```

You should be okay, my original '99 iBook needed a kernel upgrade because the mach64 drivers were missing lcd-support and my power management is still bumpy which is pretty demotivating as it worked perfectly on 2.4 last time I had Debian on this. Oh well...

---

### Post by Felix_the_Mac on 2004-11-30
Thanks. I did that and I now have installed powerprefs.
However, trackpad tapping still does not work.
Brightness and volume are working OK (didn't test eject).

To be clear, I want a tap to act as a right-mouse button click.

I also used alt+F2 to cycle through the tap modes, but still had no luck actually tapping.

I use SideTrack in Mac OS X which gives this functionality and I am desperate for the same in Ubuntu.

BTW, I found that when I restarted pbbuttonsd from the command line it complained that /etc/pbbuttonsd.conf did not exist. The file existed at /etc/pbbuttons/pbbuttonsd.conf and I linked it to /etc/pbbuttonsd.conf.

Grateful for any help :-)

---

### Post by M-Rick on 2004-11-30
It doesn't work with Apple extended keyboards :-(

---

### Post by Felix_the_Mac on 2004-12-01
[QUOTE=M-Rick]It doesn't work with Apple extended keyboards :-([/QUOTE]
 
Sorry, I don't understand your comment. 
Why should trackpad tapping be affected the what type of keyboard I use?

Thanks

---

### Post by M-Rick on 2004-12-01
[QUOTE=Felix_the_Mac]Sorry, I don't understand your comment. 
Why should trackpad tapping be affected the what type of keyboard I use?

Thanks[/QUOTE]
No I was speaking about powerpref to map my eject, sound down, sound up and mute keys with Ubuntu.

---

