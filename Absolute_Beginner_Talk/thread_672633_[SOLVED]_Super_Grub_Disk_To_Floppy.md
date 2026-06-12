---
title: "[SOLVED] Super Grub Disk To Floppy"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Frederick J. Harris on 2008-01-19
I'm trying to follow the advice at ...

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk)

to transfer the downloaded file super_grub_disk_english_floppy_0.9672.img to my floppy so as to have access to this neat sounding program.  This file was in my home directory.  I executed this command in the Terminal but nothing happened and nothing was transferred to the floppy.  I'm a newbie so could anyone give me a hint here as to why nothing happened?  Is the intent just to get this file onto the floppy or is something else more mysterious or profound suppossed to happen?  If not the latter couldn't I just use the GUI to copy it there?

Here is the command I executed...

fredharris@CODEWARRIOR:~$ sudo dd if=super_grub_disk_english_floppy_0.9672.img of=/dev/fd0
Password:
2880+0 records in
2880+0 records out
1474560 bytes (1.5 MB) copied, 0.033024 seconds, 44.7 MB/s
fredharris@CODEWARRIOR:~$

---

### Post by logos34 on 2008-01-19
no, you would have heard it writing.  Should have output something like this:

> $ dd if=super_grub_disk_english_floppy_0.9590.img of=/dev/fd0
2880+0 records in
2880+0 records out
1474560 bytes (1.5 MB) copied, 81.2364 seconds, 18.2 kB/s

is your floppy drive listed in /dev?

---

### Post by Frederick J. Harris on 2008-01-20
> 
is your floppy drive listed in /dev?


Here are the directories under /dev...

/dev/bus
/dev/disk
/dev/fd
/dev/input
/dev/net
/dev/pts
/dev/shm
/dev/snd

The third one down - fd - is a greyed out square with a curving arrow pointing down to the lower right corner.  I'm sure that is of some significance, but I don't know what it is.

Below is the contents of my /etc/fstab file..

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=19519845-5678-415b-b436-6e47dfbb8b63 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=5DB0690507EB6C88 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=3EC6-2E70  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=8854CCE454CCD65A /media/hda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=709b38f6-b1d6-4394-a6fe-fd55e64f1d5e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda        /media/floppy0  auto    rw,user,noauto  0       0

```

As you can see, the bottom line is "/dev/sda       /media/floppy0".  Indeed, if I wish to use Nautilus to view the contents of the floppy, I navigate to /media/floppy or /media/floppy0.  I attempted to use the dd command as first shown in first post but substituting /media/floppy or /media/floppy0, but this was also unsuccessful yielding the following output in the Terminal...

```

fredharris@CODEWARRIOR:~$ sudo dd if=super_grub_disk_english_floppy_0.9672.img of=/media/floppy0
Password:
dd: opening `/media/floppy0': Is a directory
fredharris@CODEWARRIOR:~$ sudo dd if=super_grub_disk_english_floppy_0.9672.img of=/media/floppy
dd: opening `/media/floppy': Is a directory
fredharris@CODEWARRIOR:~$ sudo dd if=super_grub_disk_english_floppy_0.9672.img of=/dev/fd0

```

Perhaps this should be another thread, but I'd sure like to know more about dd. I've looked it up in man/info and the best I can make out is that it does with files what strncpy (C String Function) does with memory, i.e., copies a specified number of bytes in memory to another location?  

I'd like to know how to use dd to copy this Super Grub Disk Program (which is in my home directory) to my floppy, however Ubuntu recognizes/names it.  I'm still stuck.:(

---

### Post by logos34 on 2008-01-20
> **Frederick J. Harris said:**
> 
/dev/fd

...The third one down - fd - is a greyed out square with a curving arrow pointing down to the lower right corner. 

...

/dev/sda        /media/floppy0  auto    rw,user,noauto  0       0


I thought something was screwy with /dev.  That arrow denotes a symbolic link (soft link) to the target.  Normally (as in mine) it points to /proc/self/fd

I never seen 'sda' for a floppy, but then I don't pay much attention to it anymore.

You need to use the **dd **command with the /dev/<drive>, not mountpoint.  So try it with '...**of=/dev/sda**'

Anything?

---

### Post by Frederick J. Harris on 2008-01-20
Thanks Logus! That did it!

This morning about 5 AM I woke up in a cold sweat wondering just where that dd command wrote those 1.4 MB to because it sure was reporting it wrote them somewhere and I knew it wasn't on my floppy!  I thought, good God! what if it screwed up my Win XP installation on the same disk!  So I came downstairs, booted the computer, found all was well and went back to bed.

Thanks!

Fred:)

---

