---
title: "Synaptic links missing from System-&gt;Administration after updates"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by linbie on 2006-10-23
Dear all,

I installed ubuntu 6.06 LTS everything is working great except i couldnt play mp3 files :(, but that is fine. I perform the system updates as requested by the system which took me nearly 3 hours to complete the whole process. Now a lot of the links in System->Administration are gone. One thing for sure is the Synaptic Package Manager. Can someone guide me how i can enable the link back?

And also, i have read some of the questions by other users and hoped that this can help you to help me :D !

when i run "apt-get upgrade", i get this:
jacky@qin-jacky:/$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

when i run "sudo apt-get upgrade", i get this (nothing happened):
jacky@qin-jacky:/$ sudo apt-get upgrade
jacky@qin-jacky:/$

when i run "sudo synaptic", i get this (nothing happened):
jacky@qin-jacky:/www$ sudo synaptic
jacky@qin-jacky:/www$

when i run "synaptic", it tells me this:
Not running as root, The package will run in read-only mode.You will not be able to change the package database.

when i fun "gksu /usr/sbin/synaptic", i get this:
jacky@qin-jacky:/www$ gksu /usr/sbin/synaptic
jacky is not in the sudoers file.  This incident will be reported.
jacky@qin-jacky:/www$

Any chance anyone knows what is wrong with my system?
Please help, any sort appreciated !!

Regards.

---

### Post by Tamil on 2006-10-23
Welcome to Ubuntu forums.

> **linbie said:**
> Now a lot of the links in System->Administration are gone. One thing for sure is the Synaptic Package Manager. Can someone guide me how i can enable the link back? Run Alacarte Menu Editor (in Accessories) & check whether menu items for Administration are unchecked.

---

### Post by linbie on 2006-10-23
Checked, it is there (attachment for confirmation).

---

### Post by linbie on 2006-10-23
I found out my problem. I broke my sudo. It has been fixed, and everything is back to normal. Thanks.

---

