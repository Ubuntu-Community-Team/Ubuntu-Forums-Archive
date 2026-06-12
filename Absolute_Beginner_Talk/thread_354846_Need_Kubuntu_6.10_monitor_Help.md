---
title: "Need Kubuntu 6.10 monitor Help"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2007-02-06
Until now I have had everything working perfectly. Then I went in and changed my password and when I re-booted I was stuck at a 640X480 screen. The System Settings recognized my new password and allowed me as administrator  but I cannot get it to change the size setting. Need help
Thanks, P.

---

### Post by taurus on 2007-02-06
Open a terminal and see if you can reconfigure your X, monitor section again.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Don't forget to restart X or reboot.

---

### Post by kindafunnylookin on 2007-02-06
[LEFT]That did not work, this is what happened:
```
peter@edgeville:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070206113527
peter@edgeville:~$ startx
xauth:  creating new authority file /home/peter/.serverauth.5642
xauth:  /home/peter/.Xauthority not writable, changes will be ignored
xauth:  error in locking authority file /home/peter/.Xauthority
xauth:  error in locking authority file /home/peter/.Xauthority
xauth:  error in locking authority file /home/peter/.Xauthority
X: user not authorized to run the X server, aborting.
xinit:  Server error.
xauth:  error in locking authority file /home/peter/.Xauthority
Couldnt get a file descriptor referring to the console
peter@edgeville:~$        
```[/LEFT]

---

### Post by kindafunnylookin on 2007-02-06
OK--```
startx
``` did not change anything but a reboot did, thanks to pricechild.
P

---

