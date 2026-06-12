---
title: "NTFS - Read-only file system"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Bograth on 2007-07-21
After a tricky install I finally get 7.04 working, by the help of a friend get's started with synaptic, Automatix and some other small stuff.

But now I've come to a halt.
I'm trying to make "Fildisk 3" into chmod 557 to be able to use my storage-device. (want to save files from bitorrent / DC to it) but when i try i get:
```

bogey@bogey:/media$ sudo chmod 557 Fildisk\ 3
chmod: changing permissions of `Fildisk 3': Read-only file system
```

As I read ntfs-3g was supposed to be installed with ubuntu 7.04 but anyways i followed these guides to try and fix it:

[http://ubuntuforums.org/showthread.php?t=217009&page=74](http://ubuntuforums.org/showthread.php?t=217009&page=74)

and since I've installed a AMD64 version of ubuntu also this:
[http://ubuntuforums.org/showthread.php?p=1545618#post1545618](http://ubuntuforums.org/showthread.php?p=1545618#post1545618)

Nothing happened i still get "Read-only file system"
Now I'm all out of ideas, could anyone give me some pointers/help with this problem?

Again the "Fildisk 3" is a NTFS formatted harddrive, for clarification.

Thanks!
Bograth

---

### Post by aktiwers on 2007-07-21
Look here:
[http://ubuntuforums.org/showthread.php?t=503400](http://ubuntuforums.org/showthread.php?t=503400)

Maybe that will help you?

---

### Post by Bograth on 2007-07-21
For some reason I can't check internal devices... any idea where the problem lies?

---

### Post by FleetAdmiral74 on 2007-07-21
For my 2 cents, I have to suggest not using Automatix. It can only cause problems in the furture

---

### Post by Bograth on 2007-07-22
But how do i fix it then?

I got 3 hardrives

HDD 1 : ext3 250gb S-ATA (with Ubuntu 4 partitions incl. swap)
HDD 2 : NTFS 200gb IDE drive
HDD 3 : NTFS 200gb IDE drive

When I installed Feisty Fawn it wouldn't let me have a partition larger than 200gb it said "can't have end before the start" and then i had to partition them again.

---

