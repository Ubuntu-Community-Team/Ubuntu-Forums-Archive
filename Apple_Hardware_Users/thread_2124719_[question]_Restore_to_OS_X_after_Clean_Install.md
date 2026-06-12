---
title: "[question] Restore to OS X after Clean Install?"
date: 2013-03-11
forum: Apple Hardware Users
---

### Post by PerplexxdYet on 2013-03-11
I'm wondering, If I decided to completely erase my MacBook Air's 128GB SSD and load Ubuntu 12.10 on there, could I restore to OS X? Will I still be able to use CMD+R to get to OS X Recovery and reset my computer? Thanks in advance.

---

### Post by magical2hobo on 2013-03-11
If you don't delete the recovery partition while installing Ubuntu you should be able to restore OS X, but your best bet would be to use an external hard drive and use Clonezilla to clone your OS X install. Then you have a garenteed way to revert back to OS X if you don't like Ubuntu.

---

### Post by jhohisel on 2013-03-13
Yes, CMD+R works even if the restore partition is deleted, however you must have an internet connection to be able to use this feature.
I would definitely recommend making a backup of your computer though, time machine works great for this and can be restored from using CMD+R.

---

