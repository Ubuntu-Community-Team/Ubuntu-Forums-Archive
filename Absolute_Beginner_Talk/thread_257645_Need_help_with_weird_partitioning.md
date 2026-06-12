---
title: "Need help with weird partitioning"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2006-09-14
Hi!  I am running the Ubuntu LiveCD now.  I need to partition manually, but the structure of the disk looks odd:

/dev/sda1    ntfs    141.53 GB total    14.23 GB used   127.30 GB unused boot
unallocated  unallocated 7.84MB total   ---             ---
/dev/sda2    fat32   7.51 GB total      ---             ---   lba

The last partition is my HP Recovery partition, and it also has some sort of yellow triangle warning sign next to its mount point.  What should I do?  Oh, and "lba" was listed under the heading of "flag".  Thanks! ^_^

---

### Post by Darklighter137 on 2006-09-14
Please help. =(

---

### Post by Sef on 2006-09-14
> /dev/sda1 ntfs 141.53 GB total 14.23 GB used 127.30 GB unused boot
unallocated unallocated 7.84MB total --- ---
/dev/sda2 fat32 7.51 GB total --- --- lba


/dev/sda1 has ntfs as its file system.  Of the 141.53 GB of the hard disk, 14.23 are being used and 127.30 GB are unused: free to be written to.  Boot means that this is the partition that it starts up from.

7.84 MB are unallocated means there is no file system set up on them.  

/dev/sda2 has fat32 file system and uses 7.51 GB.  As you said, 'it is your HP Partition'.  The flag is warning you not to change the partition size as you could mess up the recovery partition.

Wouldn't worry too much about the unallocated sector.  Run a disk check and see if all is ok.  Most likely, just a glitch occurred when setting up the system. (Didn't read the disk size correctly.)

---

### Post by Darklighter137 on 2006-09-14
How can I run a disk check?

---

