---
title: "Strange output following df -h command?"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-05-20
Hi everyone,
I updated my Breezy and ran df -h:
> Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              14G  6.3G  6.8G  49% /
tmpfs                 245M     0  245M   0% /dev/shm
tmpfs                 245M   13M  232M   6% /lib/modules/2.6.12-10-386/volatile
/dev/hda1              13G  4.1G  8.9G  32% /media/hda1
/dev/hda5             9.8G  977M  8.9G  10% /media/hda5


What is this **tmpfs                 245M   13M  232M   6% /lib/modules/2.6.12-10-386/volatile**
Is it necessary? Should I remove it? If yes, how?
Thanks for your help.

---

### Post by garner_nc on 2006-05-20
I'm not sure but I expect it's something to do with some type of swap system. Especially being named tmpfs (temp file system ?). My machine shows the same line using this command. Digging around in the directory looks like its storing kernel modules that are in use on the system. I would NOT delete it.

All the Best,
Doug White

---

### Post by xyz on 2006-05-21
Thanks Doug.
Some kind of explanation here?:
[http://www.kplug.org/pipermail/kplug-general/2005-December/001340.html](http://www.kplug.org/pipermail/kplug-general/2005-December/001340.html)

---

