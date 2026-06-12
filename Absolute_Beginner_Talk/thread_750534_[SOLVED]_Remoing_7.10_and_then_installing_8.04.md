---
title: "[SOLVED] Remoing 7.10 and then installing 8.04"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by R6V2 on 2008-04-09
I need to know exactly how I would (safely) remove Linux Ubuntu 7.10, but leave my partition still open the (50%), and then install the beta 8.04?:confused::confused:

Sorry if this is a newbie question!

---

### Post by alnhntr29 on 2008-04-09
What else do you have on the drive, if nothing else, then if you are using a live cd, just install over 7.10. Or you can use the manual option on the partition choice screen and install the base system into your existing partition and leave your swap intact.

hope that helps.

---

### Post by Het Irv on 2008-04-09
> **R6V2 said:**
> I need to know exactly how I would (safely) remove Linux Ubuntu 7.10, but leave my partition still open the (50%), and then install the beta 8.04?:confused::confused:

Sorry if this is a newbie question!

What do you mean by "leave my partition still open the (50%)"  If you mean how to install 8.04 without changing how your drive is partitioned then when you get the Live CD there should be an option to install Ubuntu to an existing partition.  As long as you pick the correct partition, 8.04 will overwrite 7.10 by reformatting the partition.

---

### Post by aeiah on 2008-04-09
what i always do is this:

- backup configuration files for things like exaile, mplayer, conky, my theme and my compiz settings

- backup other useful files that are in my home folder like personal documents and notes to myself

- boot up the livecd and start installing, and select to manually configure partitions, so i can format my ubuntu root and home partitions, and to point root to root and home to home

i assume you have windows on the other 50%? if that is the case, or if you have anything else of importance, just take note of which one is gonna be the one you want to overwrite. if its windows, the windows partition will be ntfs, so its pretty easy to tell which one it is.

---

### Post by SunnyRabbiera on 2008-04-09
I would hold out to be honest with you if you want to give hardy a shot, its beta so its not ready for common use yet.

---

### Post by R6V2 on 2008-04-09
Well thanks guys, I think I might just hold-off until theres a new stable release. But yeah, I got windows on the other half just for games and stuff that linux cant do :( . So, I'll wait until a new stable version is released, and then install over 7.10 :) Thanks everyone!

---

