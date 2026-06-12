---
title: "Can I transfer my exisiting dapper to new drive?"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by skew on 2006-12-23
I have two SATA hard drives in my system. Currently I have dapper and XP on the same drive and storage on the other. Now I require more space for linux and want to keep one drive for XP and use the other drive for dapper alone.  After wiping and repartioning the storage drive to ext3 Is it possible to transfer my exisiting dapper paration from the first drive over to the second? If so what method works best for this and will everything work as before or will there be lots of tweaking required to get it working?  

Thanks all,

Steve

---

### Post by steve.horsley on 2006-12-23
Don't forget you want a swap partition.

As far as I know, you could copy your entire Dapper partition contents over (using **cp -a** as root) and would then have these 3 problems to fix up:
1) GRUB on the MBR would need reinstalling to look at the new disk for its files
2) /boot/grub/menu.lst would need editing to refer to the new disk
3) /etc/fstab would need editing for the new root and swap locations

There may be more problems - I don't know. If you are happy you can fix the above problems, it may be worth a try. If not, it may be safer to use the "alternate" installer to do a new install to the new disk and then copy your /home directory contents across before deleting the original partition.

---

### Post by ajgreeny on 2006-12-23
Also worth having a look at *partimage* which will produce an image of the partition and let you copy it to another partition.  You will still have a problem with the editing needed of grub as mentioned by steve horsley, and you certainly need a swap fo 1-2 GB.

---

### Post by skew on 2006-12-23
Thanks guys.  I need the space for my Mythtv.   It's because of all the trouble that I had installing and setting up Mythtv in the first place that I did'nt want to have to go through that nightmare again anytime soon. 

 I'll look into partimage.

Cheers,
Steve

---

### Post by Patrick-Ruff on 2006-12-23
the great thing about linux, no files are hidden from you, all you gotta do is basically just copy your whole hard drive to a tar file, move it to the next hard drive, decompress and overwrite all files on the new partition, then it will be /perfectly/ adapted.

---

