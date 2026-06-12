---
title: "How to restore in 7.04 the xorg.conf?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Unetwork on 2007-04-27
When I read, I started up with the live CD, the xorg.conf there is nothing!
I have a backup but whatever I try I can't even get into /etc/x11 in the recovery text mode
Now I don't no how to mound or to get rights from the live CD into my login account and password
I tried the sudo dpkq-reconfigure xserver-org command but no success
I tried the startx answer: no screens found
I tried the sudo cp /etc/x11/xorg.config.bbackup /etc/x11/xorg.config but no success

---

### Post by Kobalt on 2007-04-27
Xorg 7.2 has this new feature : when you delete the xorg.conf file it will regenerate a new one with default settings hopefully working on many hardware. You can try this...
```
sudo rm /etc/X11/xorg.conf
```

PS: don't forget the capitals (ex. X11), Linux is case sensitive

---

### Post by joriad on 2007-04-27
It should read "sudo dpkg-reconfigure xserver-xorg" instead of "sudo dpkg-reconfigure xserver-org" also as kobalt had stated that x11 should be capitalized thus it would be X11.

---

### Post by Unetwork on 2007-04-27
thanks will give it a new try..

---

### Post by Unetwork on 2007-04-27
Thanks guys I am back, now again trying to figure out how to make my ati radeon 9250 work with dual screen

---

### Post by NRios on 2007-05-04
> **Kobalt said:**
> Xorg 7.2 has this new feature : when you delete the xorg.conf file it will regenerate a new one with default settings hopefully working on many hardware. You can try this...
```
sudo rm /etc/X11/xorg.conf
```

PS: don't forget the capitals (ex. X11), Linux is case sensitive

I deleted (actually renamed, to be safe) /etc/X11/xorg.conf, and when X restarted it did not regenerate the file, but went on working perfectly without it. Not only that, but now it *feels* faster! I enabled the 3D effects, and they work fine too.

It popped up with the default US keyboard, though, so I had to choose the spanish keyboard in the gnome control panel -- I guess X could not find by itself that setting that it previously got from xorg.conf.

The setting I've lost and cannot reenable is the use of the sroll buttons on the trackpad; that is gone with xorg.conf, and there is no control panel in Gnome to reconfigure it. A USB mouse with scroll wheel is instantly recognized and works fine, though.

BTW, this is on a portable with a Radeon R250 chip that is recognized as a Mobility FireGL 9000.

---

