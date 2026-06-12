---
title: "[SOLVED] Screen Resolution"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Valthinos on 2008-02-20
I just turned on Ubuntu and my screen resolution is maybe 800 x 600.. I don't know how this happened, how do I change it back to 1280 x 1024?

---

### Post by steve-shinn on 2008-02-20
system>preferences>screen resolution

---

### Post by Valthinos on 2008-02-20
I can't click on my System for some reason, it just opens up Pidgin cause that's the icon that's usually beside it but is now behind it.

---

### Post by OffAxis on 2008-02-20
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

with that you can limit the possible screen resolutions or force it (by only selecting one possible resolution) to what you want.

---

### Post by lswest on 2008-02-20
also <alt>+<F1> can be used to open the menu, right twice to system, down one, right, then find screen resolutions^^

---

### Post by Valthinos on 2008-02-20
Thanks for the Alt f1 tip. However, in screen resolutions,it only gives me 640x480, nothing else. Also, my Internet isn't working, but I'ts working when I boot into windows.

---

### Post by OffAxis on 2008-02-20
try the dpkg-reconfigure command.

---

### Post by Valthinos on 2008-02-20
I did, got the error overwriting posibly-customised configuration file; back up in /etc/X11/xorg.conf.20080220164841

---

### Post by OffAxis on 2008-02-20
it's not an error, just a notification letting you know that if you blow the reconfigure that there is a backup available in the /etc/X11/ folder (the number is a date & time stamp)

---

### Post by Valthinos on 2008-02-20
So what do I do? That just pops up and nothing happens.

---

### Post by OffAxis on 2008-02-20
then run it without the -phigh switch;

```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Valthinos on 2008-02-20
i am very lost with the command it gives me a bunch of options. Is there another way to do of? Also,my Internet isn't working..

---

### Post by Valthinos on 2008-02-20
Ah.. just had to go into restricted drivers and enable the graphics driver:). It was disabled for some reason, anyway, thanks for all the help!

---

