---
title: "Problems with Update Manager when trying to upgrade to Dapper"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Rayeth on 2006-09-24
Basically, when I try to use Update Manager, it tells me that I can upgrade to Dapper (from Breezy) but when it tries to do it, I get these error messages:

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Is there a way I can upgrade?  I also tried to boot from a disc but that failed for some reason.

---

### Post by bulldog on 2006-09-24
My humble opinion should be to use a sources.list with the Dapper repo's.

But I never did what you're going to do,I could be misstaken.

---

### Post by veloct on 2006-09-24
You can't upgrade to dapper if your sources.list is pointing to a breezy 5.10 cdrom.  You need to update your sources.list

---

