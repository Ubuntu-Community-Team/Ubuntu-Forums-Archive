---
title: "installing ubuntu to new iBook with no free space"
date: 2005-09-22
forum: Apple PPC Users
---

### Post by beewer on 2005-09-22
Hi everyone.

I recently bought new 12" iBook. I like mac os x but I have always liked linux and now I'm interested in Ubuntu.  (I've actually recently switched two of my Mandriva computers to run Kubuntu instead.) 

I would like to install Ubuntu and keep my os x.

Is there a way to install Ubuntu/Kubuntu to my iBook without reformatting/installing mac os x. Is there a working drive resizer for PPC?

And what devices I can expect to be working after install? Wlan? Audio?

---

### Post by stuporglue on 2005-09-22
> Is there a way to install Ubuntu/Kubuntu to my iBook without reformatting/installing mac os x. Is there a working drive resizer for PPC?

The best way I've found is to use CarbonCopyCloner (bombich.com) to backup the entire OSX install to an external HD, then use the OSX install CDs to partition the drive into two sections. One section is an HFS partition for OSX, the other is empty space. Boot from the external HD, and restore the OSX, then boot from the Ubuntu install CD and "use existing free space" in the installer. 

As for resizing, the version of "parted" on the Gentoo install CDs supposedly has experamental hfsplus resizing built in. You'd need to turn off journaling on your OSX partition though. I'm not sure if Ubuntu's parted includes it since it's experamental and Gentoo seems much less afraid to break stuff (that's why I'm here now!) 

> And what devices I can expect to be working after install? Wlan? Audio?
Airport extreme doesn't work yet. Audio will either work, or can be made to work fairly easily. There is no flash for PPC and Java is at version 1.4.2. 

Go for it! It's worth it.

---

