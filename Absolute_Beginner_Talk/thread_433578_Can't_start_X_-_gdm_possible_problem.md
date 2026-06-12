---
title: "Can't start X - gdm possible problem"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Bloch on 2007-05-05
My computer boots as far as the splash screen with orange loading bar that reaches the full extent no problem, then gnome fails to start.

I booted into recovery mode, entered
```
startx
``` to get to the root desktop
and after fiddling around found that entering
```
gdm
```
in the terminal restarts X and I am at my familiar desktop.

Now I was playing with BUM and I may have disabled splash, but when I got back in I opened BUM and checked: both splash and gdm were enabled, everything seems OK.

But I still think there is some initialisation script that BUM changed and now gdm doesn't start.

Does anyone know how to get my system back in order?

---

### Post by Pobega on 2007-05-05
```
sudo apt-get install sysv-rc-conf
```

Use that program to make sure that GDM starts at boot time (GDM should be checked for run levels 2~6)

---

### Post by Bloch on 2007-05-05
Pobega, I tried your solution and it didn't work.

However seeing as the problem started when I messed with BUM, I tried activating/deactivating various services there. 
When I deactivated 
Scripts for initialising and shuttinmg down the system (bootclean)
the system booted as normal next time.
It's a mystery to me why deactiviating services should solve the problem, and I am not sure if this is a satisfactory solution.

The service
Scripts for initialising and shuttinmg down the system (stop-bootlogd-single)
is activated - maybe these two services with the same description clashed with each other?

I'm not too fond of BUM now - there is no information given on what the services do and what might happen iof you turn them on or off. In my case the problem occurred when I turned ON a service

---

