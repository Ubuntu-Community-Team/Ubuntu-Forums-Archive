---
title: "what am I doing wrong when I attempt to use the su button"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by chris_gpt on 2007-08-11
I am attempting to mount an external harddrive, which I want mounted every time I start up ubuntu.

From my experience with ximian and red hat linux I know I must alter /etc/fstab and for this I need to be superuser.  The problem comes when I type in my password (the only password I had ever set up in the less than 1 full day I've had since I loaded ubuntu).  I didn't think to plug it in as I was installing.

How do I reconfigure my account to be able to become superuser?

Thanks,
-- Chris

About my system:
powerbook "titanium"  This is a laptop

processor: 1GHz G4

HDD: 60,000,000,000bytes (58.something GB) partitioned into two equal segments (one has MacOS10.3.9 and 9.2.2 on it, the other 29+fraction GB has ubuntu 6.0.6 on it.

ports and network potential: it has 2 USB & 1 firewire port, plus a built in 802.11 wireless networkingcard and an ethernet card.  It also has a built in 56k modem.

---

### Post by SOULRiDER on 2007-08-11
Ubuntu has the root account disabled, but you can use sudo so instead of doing:
```
su
nano /etc/fstab
```

you should do:
```
sudo nano /etc/fstab
```

---

### Post by chris_gpt on 2007-08-11
Thanks, wouldn't have thought that was possible.

PS: also forgot about the sudo command (I had always used su).  It's just less typing [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

