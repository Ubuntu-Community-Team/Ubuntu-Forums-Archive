---
title: "Changing write permissions on a USB drive"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by timdarklighter on 2007-05-23
Hello - 

Here is my setup.

One desktop: Ubuntu on one partition (ext3) and WinXP on another (ntfs)

One laptop: Mac OS X 10.4.9 (hfs+) PowerPC

One Western Digital USB 2.0 External Hard Drive: 100gb hfs+ partition and 350gb ext3 partition, no OSes installed.

On the USB drive, I set up the hfs partition using the Mac and it works fine (read and write, no problems). I set up the ext3 partition using my Ubuntu desktop and tweaked it up to get both partitions (hfs and ext3) mounting and readable and writable.

I loaded Ext2FS onto my Mac so that I could do the same (read and write to the ext3 partition on the Mac) and Ext2FS mounts the ext3 partition just fine, but it is not writable. Does anyone know how to make it writable?

I would prefer not to make dummy admin accounts or use NetInfo Manager to change my main Mac account. Is there a simple way to change the ownership or read/write ability of the ext3 partition?

Thank you. I hope this isn't too out of line for a Ubuntu forum. :)

---

### Post by eentonig on 2007-05-23
GUI style

<alt>+F2
gksudo nautilus
Browse to "/media"
right click on the folder representing the USB Media in question
select "Permissions"
Adapt the permission for "Other" to your liking.

---

### Post by timdarklighter on 2007-05-23
Doesn't that only change permissions on my linux boot drive?. I don't have any problems getting my desktop Linux box to read/write it, but it mounts to my Mac as read-only (I have "mount as read-only" unchecked in ExtFS manager).

Thanks for the info, though. That will help whenever I add new disks.

---

### Post by timdarklighter on 2007-05-24
shameless bump.

---

### Post by monitorman on 2007-11-28
Excellent!
After a lot of fruitless searching, this post was suggested as I was about to post a new query.
This is exactly what I needed!
Thanks!

---

