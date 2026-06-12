---
title: "replacing gusty back to fiesty"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by lavikl on 2007-12-15
After a bad expirience with upgrading to Gusty, i've descided to move back to version 7.10 with a clean install.
I've made an installation CD using an ISO from Ubuntu.
when i start the installation I chose manual partioning so i could choose the Ubuntu partionions and overwrite them.
finally after i managed to do that the install program asked me if i want to import files from win XP (although windows XP is installed in a diffrent partition). for some reason i couldn't go forward from this step, it kept staying in this step without allowing me to continue, and it doesn't matter if i chose to import or not.
Is there a better way to clean the installed version of ubuntu and do a fresh start ?

(i'm using a dual OS - winxp and linux)

---

### Post by lavikl on 2007-12-15
anyone please ?

---

### Post by rsambuca on 2007-12-15
Are you sure you are using a standard Ubuntu CD?  The installer never asks to import XP files, so you must be using some other disc.

Also, please wait a day or two prior to bumping your threads.

---

### Post by lavikl on 2007-12-15
It's an ISO  CD i've downloaded from ubuntu, so i guess it's the right one.

---

### Post by fedex1993 on 2007-12-15
> **lavikl said:**
> It's an ISO  CD i've downloaded from ubuntu, so i guess it's the right one.

give us like the kernal type and what not you could try to get a screen shot of what your talking about ti could help us help you

---

### Post by AdHaR on 2007-12-15
I think you have the Live CD, because only that will ask you if you want to import your profile and settings for XP or not.

I remember when i was installing gutsy from the Live CD (I had XP installed already), it asked if I want to import settings. If I checked import settings...the installation could not go forward...so i had to uncheck it and install gutsy.

Have you tried installing using the alternate installer? I dont think the alternate installer will ask to import settings.

Another thing you can do is, assuming you have access to a windows xp cd, boot up from the winxp cd and overwrite the MBR. This will remove grub. At that point, you can login to xp and format your linux partitions using disk management, and then install linux as usual.

---

### Post by erfahren on 2007-12-15
I think the OP is talking about the "Migration Assistant" that the installer is hanging on.

Did you check the boxes to reformat the Ubuntu partition(s)? If not you might want to do that.

---

### Post by lavikl on 2007-12-16
thanks for the tips, i'll try it this afternoon.

When i check the partitions for format it won't allow me to continue for some reason.
I'll also try to get a snapshot and post it.
It is a Live CD, should i get another type of ISO file ?

thank you

---

### Post by macogw on 2007-12-16
> **lavikl said:**
> thanks for the tips, i'll try it this afternoon.

When i check the partitions for format it won't allow me to continue for some reason.
I'll also try to get a snapshot and post it.
It is a Live CD, should i get another type of ISO file ?

thank you

If you can take a screenshot, it's a live cd.  The alternate cd is text-based...no mouse

---

### Post by zabien1970 on 2007-12-16
Just wondering, in your opening post you referred to going from gutsy back to 7.10, I believe gutsy is 7.10, did you mean 7.04, If you're trying to restore or whatever typing in the wrong version could give you a few headaches.

---

### Post by erfahren on 2007-12-16
> **lavikl said:**
> thanks for the tips, i'll try it this afternoon.

When i check the partitions for format it won't allow me to continue for some reason.
I'll also try to get a snapshot and post it.
It is a Live CD, should i get another type of ISO file ?

thank you
you might have better luck with the alternate cd

in case you're not used to using it there's a good guide here: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I had an alternate CD hang on me a couple times. I figured out it was because it had problems with the network settings I entered. I learned to make a point of going back and making it skip the network setup.

---

### Post by erfahren on 2007-12-16
> **macogw said:**
> If you can take a screenshot, it's a live cd.  The alternate cd is text-based...no mouse
... obviously

---

### Post by seventhc on 2007-12-16
If you want to leave xp on, but start a fresh install of ubuntu you could boot to xp, delete the ubuntu partition then boot into the ubntu live cd and install. just choose guided on the largest continuous free space. make sure you choose that by default it is set to use the entire disk. but if you choose guided free space you should have no problems.

---

### Post by lavikl on 2007-12-16
wops you're right#-o i am using 7.04 and started upgrading to 7.10.
the situation is that currently i'm stuck in the middle of the upgrade process so that's why, after reading other threads, to start all over again and do a fresh install.

---

