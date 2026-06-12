---
title: "No Screen Detection"
date: 2007-08-11
forum: Apple Intel Users
---

### Post by lifeisrandom on 2007-08-11
I was trying to use the Live CD today for the first time, but it said it couldn't detect the screen on my 15'' MacBook Pro (using the PC CD). Any help in this area would be greatly appreciated, thank you :)

---

### Post by cyberdork33 on 2007-08-11
> **lifeisrandom said:**
> I was trying to use the Live CD today for the first time, but it said it couldn't detect the screen on my 15'' MacBook Pro (using the PC CD). Any help in this area would be greatly appreciated, thank you :)

It doesn't literally mean it can't detect your monitor / display. please give the full error message and look through the log file for more info (Anything with (EE) at the beginning)

---

### Post by lifeisrandom on 2007-08-13
Error Message:

Failed to start the x server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to to view the x server output to diagnose the problem?

There was nothing with EE at the beginning, but something with WW.

---

### Post by benanzo on 2007-08-13
This is a common problem.  It is a bug that crept up right as Feisty was being released.

When you boot the LiveCD make sure you're plugged into ethernet and that you can ping your router (or google)

Type this one line at a time in the terminal after the X server dies:

```

sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo /etc/init.d/gdm restart

# or if you're using Kubuntu type:
sudo /etc/init.d/kdm restart

```

That should start the desktop.

Good Luck!

---

