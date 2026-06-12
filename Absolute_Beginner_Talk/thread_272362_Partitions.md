---
title: "Partitions?"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by YourFriendlyGopher on 2006-10-06
Hi all, I have 2 200gb hard drives, one is formatted 100% in NTFS, the other has 139gb allocated to NTFS, 17gb for ext3, 815mb swap and a 28gb vfat partition. Now that ubuntu has pretty much become my main OS, I'm thinking about cutting down on my NTFS partitions. I've installed a program that lets me write to the NTFS, but from what i've heard it isn't such a good idea. So, I thought that I could make my vfat partition larger, but i've also heard it has it's limitations (eg, less security, limited to ~30gb?). Sooo, would an ext3 partition be better? Or can only linux write to this? I want to store some large files on these partitions so I want something that'll be safe and won't corrupt my data. Thanks for any guidance with this. :cool:

---

### Post by Kateikyoushi on 2006-10-06
You could use [this driver]("http://www.fs-driver.org/") to read and write to ext partitions from windows.

---

### Post by YourFriendlyGopher on 2006-10-06
Thanks for the reply, might give that a shot. I guess it's not possible to change the filesystem without first deleting the partition/files? What partitioner would you recommend? gparted?

---

### Post by Kateikyoushi on 2006-10-06
You have to backup the files first because you need to format the new partitions, and yes I recommend gparted.

---

### Post by mixmaster on 2006-10-06
You can safely read NTFS from linux, and ext3 from windows.  It is possible to write in both directions also but the linux NTFS read-write driver is still beta (although it apparently works very well) and the thought of giving windows access to my linux system gives me hives.

Personally, I would migrate all my windows stuff onto one drive and reallocate the NTFS & VFAT paritions on the other to linux.  For future convenience I would probably use LVM2 to consolidate these two physical paritions into one logical volume which could then be allocated as needed.  If your need for windows decreases further you can shrink the windows partitions and add the freed space to your logical volume without disturbing your linux filesystems.

To shrink/move the windows partitions you can use the gnome partition manager from linux or Partition Magic from windows

---

