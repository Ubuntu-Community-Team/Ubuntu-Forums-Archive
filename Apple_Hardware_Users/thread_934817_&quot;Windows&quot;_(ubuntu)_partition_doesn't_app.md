---
title: "&quot;Windows&quot; (ubuntu) partition doesn't appear on boot menu"
date: 2008-10-01
forum: Apple Hardware Users
---

### Post by pschulam on 2008-10-01
Hi All,

I've just partitioned the hard drive on a macbook pro in order to install ubuntu. I installed ubuntu successfully but when pressing alt to see the boot menu the ubuntu partition doesn't show up, only the OS X is shown. The ubuntu partition is displayed in disk utility but it says that it is "not mounted." I followed the instructions on this forum to install ubuntu by setting the mount point to "/". Has anyone experienced this before? If so, what am I doing wrong? Thank you very much for any help.

Best,
Peter

---

### Post by thenes on 2008-10-01
I would try to install [rEFIt]("http://refit.sourceforge.net/"). This should display both the OS X and the Ubuntu partition at start up and allow you to choose which one to boot into.

---

### Post by julie2008 on 2008-10-01
it can be performed by changing the settings in properties...
______________________________________________________________________
[Sending flowers to chicago](http://www.florist-flowers-roses-delivery.com/illinois/chicago_il.html) [low rate loans](http://www.cheaponline-loans.co.uk/) [vilafranca del penedes](http://www.vilafrancadelpenedes.com) [download ringtones](http://www.myringtoneshub.com/)

---

### Post by cyberdork33 on 2008-10-01
Install rEFIt and use the partition tool in its boot menu to sync the partitions. See this thread:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by pschulam on 2008-10-01
Thanks for your quick responses guys. Installing refit and syncing the partitions did the trick. 

Best,
Peter

---

