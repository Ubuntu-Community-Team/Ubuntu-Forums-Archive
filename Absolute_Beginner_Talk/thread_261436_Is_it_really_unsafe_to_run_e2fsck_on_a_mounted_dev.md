---
title: "Is it really unsafe to run e2fsck on a mounted device?"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by fishcake007 on 2006-09-20
Just been trying to compile the Kernel from source and I get the following error , the same thing happened when I tried to compile Wine. It only seems to happen to one file and this is when it's installing it.

```

INSTALL drivers/video/sis/sisfb.ko
cp: reading `drivers/video/sis/sisfb.ko': Input/output error
make[3]: *** [drivers/video/sis/sisfb.ko] Error 1
make[2]: *** [_modinst_] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.17'
make[1]: *** [real_stamp_image] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17'
make: *** [kernel-image-deb] Error 2

```

Anyway I suspect it's a disk error of some sort as the hd starts making some strange noises.
I've already forced a diskcheck on bootup (/forcefsck) but it didn't seem to find anything. Which I dont/can't believe. 

When I run sudo e2fsck -nv /dev/hdb1 I get the following 

```
e2fsck 1.38 (30-Jun-2005)
Warning!  /dev/hdb1 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/ contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 243666 was part of the orphaned inode list.  IGNORED.
Deleted inode 1090863 has zero dtime.  Fix? no

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -2202101
Fix? no

Free blocks count wrong for group #74 (11504, counted=11502).
Fix? no

Free blocks count wrong (240141, counted=357914).
Fix? no

Inode bitmap differences:  -243666 -1090863
Fix? no

Free inodes count wrong (1239409, counted=1207781).
Fix? no


/: ********** WARNING: Filesystem still has errors **********


  188303 inodes used (13%)
   15821 non-contiguous inodes (8.4%)
         # of inodes with ind/dind/tind blocks: 20942/234/0
 2615404 blocks used (91%)
       0 bad blocks
       0 large files

  189362 regular files
   17935 directories
    1322 character device files
    4171 block device files
       4 fifos
     442 links
    7090 symbolic links (6770 fast symbolic links)
      36 sockets
--------
  220362 files

```

So is it safe to run e2fsck without the -n command on a mounted system?
I'm runing on a laptop without access to a cdrom otherwise would have just booted from a cd and checked the unmounted file system there? 
 
Would be greatful for any help.

---

### Post by Miademora on 2006-09-20
If possible id try to boot a small Linux like [DSL]("http://www.damnsmalllinux.org/") from usb-stick and perform the filesystemcheck. You need to have access to a usb-stick and your laptop needs to be able to boot from it though.

---

### Post by fishcake007 on 2006-09-20
Thanks but my laptop is a bit too old , so my bios doesn't support this.

---

### Post by Miademora on 2006-09-21
Then its getting a bit tricky. Maybe you can temporary disable your swap partition and install a mini linux on it. Then boot from it and run e2fsck. After youre done you format it back to swap.

---

### Post by yota on 2006-09-21
Hi you can force a fsck at boot time with:
```

sudo touch /forcefsck

```
and reboot.
So you can safely have your filesystem checked and eventually repaired with ease.

Hope this helps.

---

### Post by fishcake007 on 2006-09-21
**Yoda**
> Hi you can force a fsck at boot time with sudo touch /forcefsck

Thanks Already tried the sudo touch /forcefsck option but it doesn't seem to repair the disk. It does the normal check function with a progress bar , but it doesn't actually fix anything. In the  **\rcs.d\S30checkfs.sh** the following code is listed. > fsck $spinner -T -R -A $fix $force 
> 
Man Page
(The -R tag skips the root file system incase it's already mounted RW)

Is it safe to remove the -R and try /forcefsck again? Will give it try first with an added -n tag first to see what happens.  

**Miademore**
> Maybe you can temporary fdisable your swap partition and install a mini linux on it. Then boot from it and run e2fsck. After youre done you format it back to swap.


Never thought of that , it could just work , will look into some more if the above doesn't work. Thanks

---

### Post by yota on 2006-09-21
Oh, sorry I've missed the that you mentioned /forcefsck in your first post... :redface:

Anyway it should be the right tool to check fs consistency.

> 
Man Page
(The -R tag skips the root file system incase it's already mounted RW)

indeed the root fs is mounted ro at that time, so the check actually fix what is in need.

Don't trust what fsck -n says on a rw mounted fs: the fs probably not in sync cause writes are pending, and the dirty flag is on for sure (it is set to on when is mounted and off when is unmounted). It would found errors like the one you're seeing on every (sane) system.

What fsck doesn't tell you are broken sectors, so maybe you fs is ok till you try to write to a broken area of the disk.
Have you tried smartmontools to check hd health?

---

### Post by fishcake007 on 2006-09-21
I edited the S20checkroot.sh script instead , it all worked fine perfectly with the disk mounted as read only but it reported no errors which leads me to the conclusion that running e2fsck -n from unbuntu desktop just gave me a list of false errors as the disk was in use all long. 

Now to just track down the cause of those Input/Output Errors and I'll be happy. 
 
Thanks all

---

### Post by fishcake007 on 2006-09-21
Yota : you were so right! Running e2fsck on a mounted device is plain crazy!

---

### Post by yota on 2006-09-21
There's something new to learn every day...
In man e2fsck I've found:
> 
 -c     This  option  causes  e2fsck  to run the badblocks program to
              find any blocks which are bad on the filesystem, and then  marks
              them  as  bad  by  adding  them to the bad block inode.  If this
              option is specified twice, then the bad block scan will be  done
              using a non-destructive read-write test.


---

