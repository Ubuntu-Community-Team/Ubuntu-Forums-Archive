---
title: "[SOLVED] Google Earth reboot on launch"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by ewarmour on 2007-07-27
I installed Google Earth using

wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
sh GoogleEarthLinux.bin

and when I launch the app I'm logged out and get a full screen command line screen for a second and then the login screen again. I uninstalled the app for now but what gives? I'd like to use Google Earth what is going wrong?

Thanks, E

---

### Post by soul_rebel on 2007-07-28
maybe you don't have 3d acceleration on, or some problems with 3d drivers

---

### Post by ewarmour on 2007-07-28
> **soul_rebel said:**
> maybe you don't have 3d acceleration on, or some problems with 3d drivers

That was it! Wow thanks. The nvidia graphics driver on my Dell laptop (preinstalled ubuntu) were not in use in the restricted driver manager. I turned them on and now GE work like a charm.

I had no idea what the problem was, in fact I thought those drivers were in use.   

Thanks a bunch for your help!  You rock! :guitar:

---

### Post by Dubbayoo on 2007-07-28
hmm. I'm having the same problem with the free ATI driver.

---

### Post by mgmiller on 2007-07-28
> hmm. I'm having the same problem with the free ATI driver.

The free ATI driver has only limited 3D support.  Try installing the fglrx driver instead.  You should be able to do that from your restricted drivers manager.  System > Administration > restricted Drivers Manager.

---

