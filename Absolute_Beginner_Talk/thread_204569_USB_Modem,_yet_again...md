---
title: "USB Modem, yet again.."
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by Lista on 2006-06-27
Hi,

To start off, I have a Santis USB modem and in order for it to work, I have to install the following driver: eciadsl-usermode_0.11-1_i386.deb.

Nothing wrong with that. Now since pppoe wasn't installed during the Ubuntu installation I had to do it myself, and did so. I installed the following driver: pppoe_3.5-4ubuntu1_i386.deb.

But when I try to install the modem driver I get the following dependency error:

dpkg: dependency problems prevent configuration of eciadsl-usermode:
eciadsl-usermode depends on libc6 (>= 2.3.5-1); however:
Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
dpkg: error processing eciadsl-usermode (--install):
dependency problems - leaving unconfigured

I've downloaded libc6_2.3.6-15_i386.deb but when I go to install it, i get the following error: 

dpkg: regarding libc6_2.3.6-15_i386.deb containing libc6:
libc6 conflicts with initrd-tools (<< 0.1.84.1)
nitrd-tools (version 0.1.77ubuntu3) is installed.
dpkg: error processing libc6_2.3.6-15_i386.deb (--install):
conflicting packages - not installing libc6

I'm not sure what to do next, and I need your help!

---

### Post by kenweill on 2006-06-27
Try updating your system.
The libc6 version in my system(Dapper) is 2.3.6
whereas yours is 2.3.2

Install it from Synaptic or just update it. Synaptic will do the rest for dependencies.

---

### Post by Lista on 2006-06-27
I've tried, but as stated above:

dpkg: regarding libc6_2.3.6-15_i386.deb containing libc6:
libc6 conflicts with initrd-tools (<< 0.1.84.1)
nitrd-tools (version 0.1.77ubuntu3) is installed.
dpkg: error processing libc6_2.3.6-15_i386.deb (--install):
conflicting packages - not installing libc6

this error occures.

---

### Post by Lista on 2006-06-27
It's alright now.
I followed this tutorial that obviously worked for some people:

[http://www.ubuntuforums.org/showpost.php?p=747170&postcount=6](http://www.ubuntuforums.org/showpost.php?p=747170&postcount=6)

However, when I try to start the modem I get the message that it is not found. It probably has something to do with the fact that I cannot change the sync.bin file (I have only one available).

I'm tapping in the dark here! :)

---

### Post by Lista on 2006-06-27
No matter which tutorial I follow, I end up with the same error: after I type 'eciadsl-start', in the Step 3: loading firmware, I get the 'modem not found' error. Am I missing something obvious?

---

