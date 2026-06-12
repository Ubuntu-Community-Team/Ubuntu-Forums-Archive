---
title: "QUestion about sources.list and distro"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-11-03
I've opened my sources.list file and I see that the first line goes like this

# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

whereas if from terminal I write  lsb_release -a I've got

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper.

Is everything OK? :confused: 

 thanks for help

---

### Post by compmodder26 on 2006-11-03
I take it you upgraded from Breezy to Dapper?  That line was originally meant to allow using the Breezy CD as a repository.  It is now commented out and not being used.  So, no troubles there.

---

### Post by helphope on 2006-11-03
Thanks for answering.:) 

Yes, I upgraded to breezy.

Commented out is meant by # and It means that the line is not taken into consideration. Am I right?

---

### Post by jeffathehutt on 2006-11-03
Yes, that's right.

---

