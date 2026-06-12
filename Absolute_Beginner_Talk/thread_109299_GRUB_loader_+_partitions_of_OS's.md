---
title: "GRUB loader + partitions of OS's"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by nerdman on 2005-12-28
Hello all.

I just acquired a 80 gigabyte harddrive. ...I was previously running on a 4gb. So... I used the Windows XP setup to chop it into 3(5gb) partitions, with a fourth 60ish gigabyte 'storage' drive.

Partition 1 for **Windows XP**.
Partition 2 for **Windows 98**.
Partition 3 for **Ubuntu Hoary Hedgehog**.

Is that going to work? Is there an order I should install the Operating Systems? I want to get all my OS's working before I go crazy installing stuff... Windows depends on drive letter and that Ubuntu partition might not show up, changing my storage from H: to G:. (Which is why windows fails.)

Then, how do I use the GRUB loader to make a pimpin' OS select screen? I think that thing is cool as hell, can't wait to show it off at a LAN party.

Also as a side note, I'm wondering if anyone has ever used Knoppix... I came in possession of an install CD for it and I'm scared to try it without a second oppinion >.o

---

### Post by Suger on 2005-12-28
It should work, if your big partition is FAT32. If it's NTFS, Ubuntu will be able to read it, but not to write to it.

And leave the grub work to the ubuntu installer, it will do it for you.

---

### Post by [Nirvana] on 2005-12-28
maybe you can install them in that order, because Grub searches for other operating systems when it is installed, and (would indexes be the right word?) indexes them.

---

### Post by nerdman on 2005-12-28
Hmm... Windows 98 won't install because my 'boot partition' is NTFS.

Windows XP won't format my 60gig partition to FAT32, only NTFS. ...I'll find a way around it.

So, I guess I gotta fdisk again.... But this time I'm more prepared.

---

### Post by psusi on 2005-12-28
Just make one partition at a time, as needed, rather than trying to set them all up first.  

Start by installing 98.  Create a partition and format it for fat32, and install.  Once 98 is set up, boot off the XP install cd and create a new partition and install XP to that.  This should be NTFS.  Finally, install ubuntu while leaving some free space unpartitioned.  Do this, and everything should just work.  

Then you should be able to use the remaining free space to set up another partition and format it as fat32 to share data between ubuntu and windows.  You can do this from within ubuntu using gparted.  

By the way, why do you want both 98 and xp?  And why Hoary?  It is old, the current stable release is breezy.

---

