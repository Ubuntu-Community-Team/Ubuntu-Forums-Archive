---
title: "OS X Disk Utility on Ubuntu?"
date: 2006-12-04
forum: Apple PPC Users
---

### Post by funk19 on 2006-12-04
Most of you will know that in OSX's Utilities folder is the Disk Utility application that allows you to verify disk permissions on your OSX disk. Does anyone know if there is anything similar to this on Ubuntu?

I have no doubt I screwed up my file and folder permissions on most of my Ubuntu system and I want to know if there is any "easy" way to verify and fix any errors on the file system.

---

### Post by dpny on 2006-12-04
Have your tried fsck?

Look [here](http://www.die.net/doc/linux/man/man8/fsck.8.html) or [here](http://www.die.net/doc/linux/man/man8/fsck.ext2.8.html).

---

### Post by funk19 on 2006-12-04
> **dpny said:**
> Have your tried fsck?

Look [here](http://www.die.net/doc/linux/man/man8/fsck.8.html) or [here](http://www.die.net/doc/linux/man/man8/fsck.ext2.8.html).

I haven't tried this yet but I'll give it a bash. Thanks for the tips!!!

---

### Post by AlphaMack on 2006-12-04
Yes, the OS X Disk Utility is just a front-end for fsck and diskutil.  You should also consider keeping your /home on a separate partition should you mess something up with the base system and need to reinstall.

---

### Post by funk19 on 2006-12-05
> **alphasubzero949 said:**
> Yes, the OS X Disk Utility is just a front-end for fsck and diskutil.  You should also consider keeping your /home on a separate partition should you mess something up with the base system and need to reinstall.

Well the great news is that I did mess my system up quite badly with the permissions and ownerships and after spending nearly 24 hours trying to repair it I gave up and did a fresh install.

Thats one of the things about linux.... if you don't fully know what you are doing you can really mess things up quite badly and I can tell you now I'll never touch file permissions again!!!

Now that I have my new fresh ubuntu install how would I go about creating a partition to an already setup system so that I can keep my home folder on a separate partition?

I don't want to mess things up again seeing as I am starting from scratch again!!!

---

