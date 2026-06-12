---
title: "How best to install Ubuntu"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2006-10-03
I have two hard drives one with XP and the other, which has three partitions, one of these partitions I use for photo storage.  The other two partitions on drive two are empty.  How can I set this so that I place an Ubuntu installation on the two partitions of the second HD please?

---

### Post by guysmiley25 on 2006-10-03
There are a few ways you could do this but it does depend on some things

Do you want to access your photos in both XP and ubuntu?
Do you want to have a partition that can be accessed by both XP and ubuntu?

I think you need at least 2 G for ubuntu so keep that in mind also

What you could do when you boot to ubuntu live cd or alt install setup as normal till you get to the partitioner then make one of your free partitions a etx3 partition and set the mount point as "/" and use your other free partition setup as fat32 and mount as /docs or somthing like that. and at last mount your photo partions as say /photo or somting like that.

Also remeber you need a swap partition so you made need to delete your free partitons first so you can make a swap partition.

It maybe possible that your photo partition is NTFS and i've heard that linux can only read NTFS but im not sure.

you can convert NTFS to FAT32 in some cases with pqmagic.

Hope that helps its my first time helping.

---

### Post by xyz on 2006-10-03
Try this for dual booting:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by a.v.l on 2006-10-03
> **xyz said:**
> Try this for dual booting:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)


Thanks Guys, if I write/save all images which are stored on my present XP HD - to a DVD Disc.  Will I be able to view those DVD photos in Ubuntu later?

---

### Post by xyz on 2006-10-03
Don't see why not! Make sure you have the codecs and everything:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

