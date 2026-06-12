---
title: "What does this error mean"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by hardfire_avk on 2006-06-29
What does this mean and how do i resolve this

> 

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems




---

### Post by lamego on 2006-06-29
It means APT is trying to update the files available from the CD repository but the path is no longer available.
If you dont plan to use the CD againt and prefer to get all the packages from the network (even those that could be available on the CD) just comment the CD related line on /etc/apt/sources.list .

---

