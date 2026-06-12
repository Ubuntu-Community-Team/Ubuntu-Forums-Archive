---
title: "USB Drive Formatting Problems"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by landsg on 2006-05-07
Hello:

I have been trying to get write permission to my Seagate USB 80g external drive.  It was formatted in NTFS, which I understand Linux cannot write to.  

So I installed Gparted and re-partitioned a couple of times trying different things.  The only thing so far that lets me write files to it is Linux-Swap file system.  Ext2 or Ext3 still do not allow me permission to write to it.

Is Linux-Swap OK to use permanently as my file system for this drive, and why doesn't ext2 or ext3 give me access?

---

### Post by ruzle0 on 2006-05-07
if you are activating the disk through gnomes System->Admin.->disks the ownership of the partiton will be to root, so you'll only be able to write to it as root.

swap is designed to hold data from ram so i'm not sure its ideal to hold anything longterm, maybe when you reboot data from ram might eventually be swapped out over data you wrote there before. To be honest i'm not expert on the implications of this situation but i'd get it partitioned into something designed for what you want.

sorry, edited out a bit as i'm talking out of my bum. just checking some man pages

---

### Post by ruzle0 on 2006-05-07
if you mount the partition [formated as ext3] then 'cd' to it, use 
sudo mkdir DIRNAME
you can then change the ownership and or the permisions of the directory to allow you to write.
eg
sudo chown OWNER:GROUP DIRNAME
and chmod command will change permissions.
Its probably for security that only root can write to the root of the partition and they can then grant the access they to those files

---

