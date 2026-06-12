---
title: "Using Acronis Trueimage on my PC : will it pick up Ubuntu partition ?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Browser_ice on 2006-07-16
I have low-formatted both my HD
I have re-installed Win-XP with all updates and a minimal set of software I use.
I have re-installed Ubuntu 6.06 with the CD I received through mail.

I want to do an image of my whole PC on DVDs so the next time I have to do this again, I will simply boot from a rescue CD and apply the image back on my PC for a basic installation.

Now to do this, I have downloaded the Acronis Trueimage v9.0 Trial version.  I have chatted with an Acronis agent who told me I could do all this (all HD, all partitions) even if trial version expires. 

Agen also sent me link below for all supported O/S :
[http://www.acronis.com/homecomputing/products/trueimage/requirements.html]("http://www.acronis.com/homecomputing/products/trueimage/requirements.html")


Now before proceeding, I want to have a confirmation that Ubuntu will be imaged by Trueimage V9 trial.

---

### Post by rbalfour on 2006-07-16
Yes it will work...Acronis is LINUX...([http://www.ubuntuforums.org/showthread.php?t=212164](http://www.ubuntuforums.org/showthread.php?t=212164))
But don't think you can burn directly to a dvd via Acronis. tried it and didn't work. USB stick/ USB Hard disk / Network work great.

---

### Post by clarkth on 2006-07-16
> **rbalfour said:**
> Yes it will work...Acronis is LINUX...([http://www.ubuntuforums.org/showthread.php?t=212164](http://www.ubuntuforums.org/showthread.php?t=212164))
But don't think you can burn directly to a dvd via Acronis. tried it and didn't work. USB stick/ USB Hard disk / Network work great.

The new version of Acronis Home states that it now has built in DVD burining software so you can burn the image straight to a DVD.  I haven't upgraded yet, but this is one feature I'm glad they included.

---

### Post by noynac on 2006-07-16
I have used TrueImage 8.0 to restore my Ubuntu partition on a WinXP/Ubuntu dual-boot. It worked fine.

I have read that the grub boot loader would not work for some after a TrueImage restore of a Linux partition/disk. A not-so-simple fix in this event is to restore the grub. I have been researching the best method on how to accomplish this, but there are no great resources. The best is:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub-install%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub-install%29)

You may also want to review some of the pertinent threads on the Acronis forum at:

[http://www.wilderssecurity.com/forumdisplay.php?f=65](http://www.wilderssecurity.com/forumdisplay.php?f=65)

There are no firm answers on this issue that I have been able to find.

---

### Post by Browser_ice on 2006-07-26
Well the problem with True Image of Acronis lies in the build 3677. Anything before that for version 9 will not write to DVD directly.

The current Trial version is something like build 3633 and does not write to DVD properly. 

I had long discussions with Acronis. I managed to have a 15 day trial of build 3677 to at least try to create my image of my whole PC.

---

### Post by catlett on 2006-07-26
NTFS is experimental but if you want a definate image backup of Ubuntu, Partimage is the app. [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

