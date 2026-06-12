---
title: "Only starts in safe graphics mode"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by getiton on 2008-01-01
I have no previous experience, but I recently decided to try Gutsy on an extra laptop. 

The laptop screen has a crack in it, so I decided to use a monitor. 

I tried to set the screen options so that the plugged in monitor would be the default screen, and set the model and resolution. i restarted the computer, and now, it only starts in safe graphics mode.

Any suggestions on how to fix this and get it working the way i intended?

The laptop has a Radeon Xpress 200m video card

---

### Post by jcats on 2008-01-01
I am also a new user to Ubuntu, but hopefully I can get you started in the right direction. I have had the same issue of setting everything up and after the rebooot, low graphics mode:mad:
ATI and Ubuntu do not get along real well. But I have found the program  Envy  (you will have to download it from the web) has been very helpful in getting video drivers to work. Just Google Envy, download the .deb, and double click the download and it will install itself. You will have to have your install disc handy, as it will need some drivers from it.

Good luck;
jcats

---

### Post by getiton on 2008-01-01
still loading in safe graphics mode when i reboot...any other help?

---

### Post by JoshuaRL on 2008-01-01
Try this:

```

sudo dpkg-reconfigure xserver-xorg

```

That will try to reconfigure xserver for your graphics card by autodetecting your hardware and asking some simple questions of you.  You will probably have to use the open source DRI drivers.  If you have any questions just ask.

---

