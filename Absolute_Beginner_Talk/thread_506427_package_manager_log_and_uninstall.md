---
title: "package manager log and uninstall?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by scholzilla on 2007-07-21
Today I used package manager to install new upgrades. One of these has completely disabled my sound (a [familiar problem]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/121105") for me). I would like to:

1. generate a list of all the updates that I made (is there a log somewhere?)

and 

2. uninstall all of them

Please help.:mad:

---

### Post by forestpixie on 2007-07-21
in synaptic file>history

---

### Post by sad_iq on 2007-07-21
Don't really know how to generate the list...but there is a log: **/var/log/dpkg.log** . It has all entries sorted by install date and all that...Hope it helps!!!

---

### Post by forestpixie on 2007-07-21
if you do the synaptic file - history thing - you can get the day/time files - highlight and paste into a text editor - i assume then you could make a list of the updated files as well - I assume you'll need to replace the files with the older version

---

### Post by scholzilla on 2007-07-21
My new best friends. Thanks.

---

### Post by forestpixie on 2007-07-21
hee hee- hundreds ended up with me as a best friend when I've was pulling my hair out - had to buy a wig :)

---

