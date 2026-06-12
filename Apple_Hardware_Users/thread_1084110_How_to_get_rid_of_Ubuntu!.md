---
title: "How to get rid of Ubuntu!"
date: 2009-03-01
forum: Apple Hardware Users
---

### Post by DanAtLucas on 2009-03-01
First off, I love Ubuntu. 

This laptop had no OS on it, so I put Ubuntu on it, in hopes of using it. Now, I have an OS X that I would like to load on, but I can not with Ubuntu on it!

How do I wipe my hardrive clean so I can just install the OS X???

---

### Post by howefield on 2009-03-01
> **DanAtLucas said:**
> First off, I love Ubuntu. 

This laptop had no OS on it, so I put Ubuntu on it, in hopes of using it. Now, I have an OS X that I would like to load on, but I can not with Ubuntu on it!

How do I wipe my hardrive clean so I can just install the OS X???

Load up the Ubuntu live cd and use the partition editor to format the disk, but knowing nothing about OS X, can't it deal with formatting the disk ?

---

### Post by mkvnmtr on 2009-03-01
You should be able to put the mac disk in and restart. When the yaboot or grub prompt comes up choose the disk and it should boot off or the disk. Then I think you just have to follow instructions. If you have formed a bunch of partitions in Ubuntu you might need to go to disk utility on the mac disk to fix them the way you want.

---

### Post by ForMar on 2009-03-01
Once your in the osx install screen (by doing what the above guy said) look at the top tool bar, search through them and you will find one that has disk utility as an option (I think its the middle one). Click that and you can format there.

---

### Post by DanAtLucas on 2009-03-01
> **howefield said:**
> Load up the Ubuntu live cd and use the partition editor to format the disk, but knowing nothing about OS X, can't it deal with formatting the disk ?

Where do i find the partition editor?

---

### Post by DanAtLucas on 2009-03-01
> **mkvnmtr said:**
> You should be able to put the mac disk in and restart. When the yaboot or grub prompt comes up choose the disk and it should boot off or the disk. Then I think you just have to follow instructions. If you have formed a bunch of partitions in Ubuntu you might need to go to disk utility on the mac disk to fix them the way you want.

I've tried this, but it comes up with a O with a slash through it, and I asked my mac expert friend what this meant and he said that Ubuntu is probably the problem. I figure if I get Ubuntu off, I can at least try, and if it doesn't work, I still have the Ubuntu disk to reinstall it.

I basically just need a command to wipe the hard drive that I can put into the terminal. my partition is hda I guess? if that makes any sense.

---

### Post by cyberdork33 on 2009-03-01
> **DanAtLucas said:**
> I've tried this, but it comes up with a O with a slash through it, and I asked my mac expert friend what this meant and he said that Ubuntu is probably the problem. I figure if I get Ubuntu off, I can at least try, and if it doesn't work, I still have the Ubuntu disk to reinstall it.

I basically just need a command to wipe the hard drive that I can put into the terminal. my partition is hda I guess? if that makes any sense.
Is that on the partition tab of Disk Utility?

On the Ubuntu LiveCD, gparted is: Systen > Adiministration > partition editor

---

### Post by mkvnmtr on 2009-03-02
If you can boot the Ubuntu live disk you can boot the correct mac install disk. If you are trying to use a disk from a different system it will probably never boot. If you go deleting stuff before you know for sure it is not your mac disk that is the problem you will own a nice notebook that won't boot into anything.

---

### Post by DanAtLucas on 2009-03-02
Well, we've come to the conclusion that possibly the OS X is too old, we're not sure. Either way, thank you for the help! Under System>Administration there is no Partition Editor for me, unless it has a different name that I don't know lol.

Thank you, all. I'm going to buy a legal OS X disk and see how it turns out. I'll let you all know. Thanks again :)

---

### Post by cyberdork33 on 2009-03-02
> **DanAtLucas said:**
> Well, we've come to the conclusion that possibly the OS X is too old, we're not sure. Either way, thank you for the help! Under System>Administration there is no Partition Editor for me, unless it has a different name that I don't know lol.
In your installed system it is not there unless you install it. We are talking about booting the LiveCD.

---

### Post by Alterax on 2009-03-04
> **DanAtLucas said:**
> 
Thank you, all. I'm going to buy a legal OS X disk [....]

That would be the problem...and the reason that you were able to install Ubuntu (but not OS X) with the same cd-rom drive.  It's not Ubuntu; OS X could really care less as it overwrites the drive anyhow.

OS X cd-rom disks aren't standard CD-ROMs; they use one of the HFS filesystems rather than ISO 9660.  Chances are your friend's copy got the data portion, but not the portion that contains the bootstrap and installer.

---

