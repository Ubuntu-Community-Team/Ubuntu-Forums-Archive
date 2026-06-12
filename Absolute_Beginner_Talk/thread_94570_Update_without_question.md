---
title: "Update without question?"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by Paul Casey on 2005-11-24
when my update manager (the little notifier on the top right of my default Ubuntu 5.10 install) - when it tells me there are updates... should I always apply the updates without question?  I've been doing this, applying the updates as notified. But am wondering if doing so could bring in a bad update and break my install.

I don't know if I know how to do a 'rollback' or if there is such a feature.  A few days ago one of the updates was a kernel update and I applied it without question. Is this a best practice with Ubuntu?

---

### Post by Xian on 2005-11-24
Updating a working system is never 100% safe and a lot of people will tell you the only reason to upgrade is if (1) there have been bugs fixed that correspond to issues you are also experiencing, or (2) there is a security vulnerability being applied that might affect your system. You can view the changelogs and see this information for yourself by opening Synaptic, highlighting the package(s) and choose Package > Download Changelog.

My experience with the Ubuntu packages has lead me to upgrade anything which is from an official mirror without further research, with the only exception being the kernel. I do generally wait a day or two on those to see if any critical bug reports have been filed, or if users report problems that are serious enough to warrant further review.

You can also install the package apt-listchanges which will show what has been changed in a new version of a package, as compared to the version currently installed on the system.

---

### Post by Paul Casey on 2005-11-24
[QUOTE=Xian]Updating a working system is never 100% safe . . . .[/QUOTE]

That's what I think... but the update notifier on my Ubuntu 5.10 is quite active.. So I've been learning to use it and wondering about the QA process behind it.   Thanks.

---

### Post by mirkov on 2005-11-25
The recent kernel update (2.6.12-9 to 2.6.12-10) changes only 4th number in the version. I have 2 kernel modules (ivtv, built from source and sl-modem, installed from a .deb package). Will I have to compile ivtv again and find the corresponding deb package for sl-modem after upgrading to the new kernel?

If that is true, I assume I can continue to boot into old kernel with custom-compiled modules until I find the time to update the 2 custom modules? Or will the updated nvidia package render GUI of the old kernel useless?

Is there a way to turn off update notification in upper Taskbar?

Plenty of questions. ;)

---

