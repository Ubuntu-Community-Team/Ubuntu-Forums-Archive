---
title: "macbook pro 7,1 w/ ubuntu 10.10; cannot start X"
date: 2010-11-21
forum: Apple Hardware Users
---

### Post by paulr1984 on 2010-11-21
Hi,

I've just finished upgrading from ubuntu 10.04 to ubuntu 10.10.  Note, this was not a fresh install, this was an upgrade.  I had my display working perfectly fine when I was on 10.04.  But after upgrading, I get the command line when booting into ubuntu.  When I run the command "sudo startx", I get this error:

FATAL: Module nvidia not found
(EE): NVIDIA: Failed to load the NVIDIA kernel module.  Please check your
(EE): NVIDIA:    system's kernel log for additional error messages.
(EE): NVIDIA: Failed to load module "nvidia" (module specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found


I'm using a macbook pro 7,1 which has:
    NVIDIA GeForce 320M


I need your help, please.

This is what my /etc/X11/xorg.conf file looks like now:

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Diver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

---

### Post by theSuperman on 2010-11-21
Try renaming your xorg.conf to xorg.conf.0 and see if it boots without it.

---

### Post by blueridgedog on 2010-11-22
You can also try to reconfigure the xserver:

```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by kstaats on 2010-11-23
I just picked up a MacBook Pro this weekend and was unable to get 10.10 to work ... so I installed 10.0.4 and then updated all on-board sw to the most current. Not certain if this is the equivalent of 10.10, but it does work well now.

---

### Post by paulr1984 on 2010-11-24
thanks for all your response guys!  Renaming the xorg.conf file worked.

---

