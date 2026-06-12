---
title: "Error: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY"
date: 2012-08-16
forum: Any Other OS
---

### Post by tech291083 on 2012-08-16
Hi,

My Fedora 16 32+ bit pc is giving me the following error and does not boot at all, please help me out. Fedora is the only OS the hard drive. This has happened for the very first time and the hard drive is also new and working well as far as I am aware. Thanks.


```
/dev/mapper/VolGroup-lv_root: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. 
(i.e., without -a or -p options)  

dracut Warning: e2fsck returned with 4  

dracut Warning: /dev/mapper/VolGroup-lv_root contains a file system 
with errors, check forced. 

dracut Warning: Error reading block 9437265 (attempt to read block from 
filesystem resulted in short read) while getting next inode from scan.  

dracut Warning: *** An error occurred during the file system check.  

dracut Warning: *** Dropping you to a shell; the system will try  

dracut Warning: *** to mount the filesystem(s), when you leave the shell.  

dracut Warning:   Dropping to debug shell:  

sh: can't access tty: job control turned off  

(Repair filesystem):/#

```

Following is what I have done using a BackTrack Linux 5 DVD. I booted with this DVD and tried the following in a terminal as root.  But now it says loading and Fedora never boots, it just freezes with the message "loading" on the screen, this is very annoying so please guide me as to what steps I should be taking to correct the problem. Thanks.


```

root@root:~# fsck -f /dev/mapper/VolGroup-lv_root 
fsck from util-linux-ng 2.17.2 
e2fsck 1.41.11 (14-Mar-2010) 
fsck.ext2: No such file or directory while trying to open
 /dev/mapper/VolGroup-lv_root  

The superblock could not be read or does not describe a correct 
ext2 filesystem.  If the device is valid and it really contains an ext2 
filesystem (and not swap or ufs or something else), then the 
superblock is corrupt, and you might try running e2fsck 
with an alternate superblock:     
e2fsck -b 8193 <device>






```

```

root@root:~# e2fsck -b 8193 /dev/mapper/VolGroup-lv_root 
e2fsck 1.41.11 (14-Mar-2010) 
e2fsck: No such file or directory while trying to 
open /dev/mapper/VolGroup-lv_root  The superblock could not be read or 
does not describe a correct ext2 filesystem.  If the device is valid and it 
really contains an ext2 filesystem (and not swap or 
ufs or something else), then the superblock is corrupt, 
and you might try running e2fsck with an alternate superblock:

 e2fsck -b 8193 <device>







```

```

root@root:~# e2fsck -b 8193 /dev/sda2 
e2fsck 1.41.11 (14-Mar-2010) 
One or more block group descriptor checksums are invalid.  
Fix<y>? yes


Group descriptor 0 checksum is invalid.  FIXED. 
Group descriptor 1 checksum is invalid.  FIXED. 
Group descriptor 2 checksum is invalid.  FIXED. 
Group descriptor 3 checksum is invalid.  FIXED. 
Group descriptor 4 checksum is invalid.  FIXED. 
Group descriptor 5 checksum is invalid.  FIXED. 
Group descriptor 6 checksum is invalid.  FIXED. 
Group descriptor 7 checksum is invalid.  FIXED.
..
.
.
.
.
.
.
/dev/sda2 contains a file system with errors, check forced. 
Pass 1: Checking inodes, blocks, and sizes 
Pass 2: Checking directory structure 
Pass 3: Checking directory connectivity 
Pass 4: Checking reference counts 
Pass 5: Checking group summary information Free blocks count wrong 
for group #0 (3823, counted=3816). 
Fix<y>? 




```

```

Free inodes count wrong for group #0 (2021, counted=2006). 
Fix<y>? yes  
Free inodes count wrong for group #16 (2032, counted=1990). 
Fix<y>? yes  
Directories count wrong for group #16 (0, counted=1). 
Fix<y>? yes  
Free inodes count wrong for group #32 (2032, counted=1831). 
Fix<y>? yes  
Directories count wrong for group #32 (0, counted=3). 
Fix<y>? yes  
Free inodes count wrong (128005, counted=127747). 
Fix<y>? yes  
 /dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****
 /dev/sda2: 269/128016 files (0.7% non-contiguous), 99869/512000 blocks



```

I just tried to edit the kernel line of my regular boot entry ie kernel entry (there are 3 kernels on boot menu) by adding the word "single" to the end of the kernel line and boot with this modification but then I got the following error.

```
/sbin/init: error while loading shared libraries: libudev.so.0: 
cannot open shared object file: No such file or directory"
```

Thanks.

Please help. i have tried all the tricks that I have. Will cloning this hard drive help? Thanks.

---

