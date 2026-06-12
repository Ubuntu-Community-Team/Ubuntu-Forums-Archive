---
title: "[SOLVED] How could ubuntu6.06(ext3-slave disk) &amp;amp; windows2000pro(master disk-FAT32) in"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by offline on 2007-10-11
At last, I dual booted MY computer which has 2 hard disks

ubuntu6.06(ext3-slave disk) & windows2000pro(master disk-FAT32 (and not NTFS as I wrongly knew) )

When being either in windows or ubuntu they can't interact just show the hard disk icon.

I haven't done any windows hard disk mounting on ubuntu.

Can either of my OS access(read-write) each other;s files???

New comer ubuntu(tourist) fan
offline(is online :))

---

### Post by cowkiller on 2007-10-11
I found this guide to mount Fat32 in ubuntu spanish page, I'll translate it for you.
 Hope it helps:

You have to edit the fstab firstly, so type in a command console:

sudo gedit /etc/fstab

Look for something like this:

/dev/hd* /media/hd* vfat

You have to change whatever is after vfat for 

umask=000 0 0
 
pressing tab between each zero. Save the file.
Again, in the console, type:

sudo umount -a

sudo mount -a

You should be able to write/read in Fat32. Good luck!

---

### Post by offline on 2007-10-11
> **cowkiller said:**
> 

You have to edit the fstab firstly, so type in a command console:

sudo gedit /etc/fstab

Look for something like this:

/dev/hd* /media/hd* vfat



There **isn't** any 

```
 /dev/hd* /media/hd* vfat
```

I right clicked and activated the windows drive from "computer" in nautilus but it is 0 bytes and couldn't be mounted from GUI.


HELP!

---

### Post by offline on 2007-10-11
Now there weren't any /media/hd* files so

sudo mkdir /media/win1  (mount point creation. we access from here our window files)
sudo gedit /etc/fstab       (edit fstab to add see below)

added 

/dev/hda1 /media/win1 vfat users,rw,owner,umask=000 0 0 

 as long as hda1 is my windows disk... vfat is fat32 partition of windows drive


Thanks anyway.

---

