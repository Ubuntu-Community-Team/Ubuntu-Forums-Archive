---
title: "/ partition is full, but have space in /home"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Xiong Chiamiov on 2007-12-07
So, I read somewhere that I should create a swap partition equal to the size of my ram, a root partition of 2-3 gigs, and the rest being /home, which I did (making /home 271 gigs).  The problem is, the 3 gigs of / is full after 2 days of installing apps.  It seems to me that I should have installed it all on just one partition, perhaps?  The question is, how do I go about fixing this.  All I've done so far is install the latest version of alsa, wine, guildwars, pidgin and firefox, which can all be redone now that I know how to do it.  Granted, I'd prefer not to reinstall it all, but I can I need be.  This is on Kubuntu Gutsy.

---

### Post by llamakc on 2007-12-07
You can get rid of downloaded deb files by running:

sudo apt-get clean

in the Terminal.

---

### Post by taurus on 2007-12-07
You can clean the cache with

```
sudo apt-get clean
```
Otherwise, you can use GParted LiveCD to resize your partitions, making / a little larger.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by DirtDawg on 2007-12-07
Ah, thanks guys :D

---

