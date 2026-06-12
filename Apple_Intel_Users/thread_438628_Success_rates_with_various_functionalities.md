---
title: "Success rates with various functionalities"
date: 2007-05-09
forum: Apple Intel Users
---

### Post by ronocdh on 2007-05-09
Hey all, just wanted to get a feel for who's tried what and had success. I ask you to please post with your explicit system specs so we have a good idea what we're dealing with--and hopefully it'll aid in troubleshooting, if necessary!

*Edit: remember to check all that apply! Also, I thought there'd be way more options to provide... I ran out of ideas quickly. =( Post anything I forgot.*

---

### Post by benanzo on 2007-05-10
good idea.

My system:

MacBook with Intel Core Duo 2.0 Ghz, 2GB Corsair RAM, 160 GB Hitachi SATA HDD.

I have 4 partitions:

/dev/sda1 / (feisty)
/dev/sda2 /swap
/dev/sda3 /home (feisty)
/dev/sda4 / (gutsy)

I have the 80 GB disk that came with the machine setup with OS X, WinXP and Feisty, (although I blow it away frequently as I experiment with new partitioning schemes.)

Overall everything is as functional as it is under OS X, with the exception of battery life.  I get 2.5-3 hrs with everything set for maximum power saving in gnome-power-manager.

Beryl is great but some of the plugins (blur effect, rain) make my system unusably slow.

I can write to the OS X partition from Ubuntu if I disable journaling and use sudo.

---

### Post by Zelut on 2007-05-10
can you post any information on how / where to disable journaling in OS X?

---

### Post by ronocdh on 2007-05-10
> **kuyaedz said:**
> can you post any information on how / where to disable journaling in OS X?
Off the cuff, I thought it was as simple as flipping a toggle in Disk Utility. I am not in OS X atm, though, and so I'll check later on.

---

### Post by benanzo on 2007-05-11
I disabled journaling in the OS X terminal with *diskutil*

I think it was:

```
sudo diskutil disableJournal disk0s1
```
or whatever your OS X partition is.

just do diskutil without an argument to see the available options.

really good info on the gentoo-wiki including how to compile Apple's HFS+ tools for Linux so you can make HFS+ partitions and add robust read/write support to your kernel.
[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

(gentoo has the best wikis IMO...sorry debian)

---

### Post by Zelut on 2007-05-11
I did find out, for those of you that want to do it the GUI way, that a menu item appears to 'disable journaling' if you press and hold the mac option button (bottom left).

---

