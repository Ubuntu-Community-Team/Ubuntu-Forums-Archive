---
title: "Read only disk ?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-06-08
Error:"Permissions could not be changed because it's on a read-only disk" :confused:

---

### Post by NeoLithium on 2007-06-08
What were you trying to do when you got the error?

---

### Post by dannyboy79 on 2007-06-08
does your fstab have the ro option within it? OR is this driver we are talking about a NTFS drive? when you post, you should really provide more info as this could be any number of things.

---

### Post by Najand on 2007-06-08
Post your /etc/fstab and the output of [FONT="Courier New"]sudo fdisk -l[/FONT] command.

---

### Post by Drakkor on 2007-06-08
it's on sdb3. here's  the fstab

/dev/sdb3       /media/sdb3     ext3    defaults,errors=remount-ro                0       1

I'm trying to delete a folder !

---

### Post by Najand on 2007-06-08
errors=remount-ro means if some error happens, then mount it as a readonly file system. Anyway why do you have 1 for the 6th parameter (the <pass> parameter). Change it to 0 (Zero). Also change "errors=remount-ro" to "rw" and remount your filesystem.

---

### Post by Drakkor on 2007-06-08
Here's the whole fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5fd7dfef-05c9-415b-87c3-61a0062702b4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=1fe5a20e-72bf-4514-aca9-cc053187c8c9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb3       /media/sdb3     ext3    defaults,errors=remount-ro                0       1

The fdisk

Disk /dev/sdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+  83  Linux
/dev/sdb2            7113        7299     1502077+   5  Extended
/dev/sdb3            2551        7112    36644265   83  Linux
/dev/sdb5            7113        7299     1502046   82  Linux swap / Solaris

---

### Post by Najand on 2007-06-08
Did you try to change "errors=remount-ro" to "rw" and remounting it? Don't forget to change "1" to "0".

---

### Post by Drakkor on 2007-06-08
I thought I did, but it came back like before !
It's been awhile since editing fstab, I made the changes, hit CtrlX, the yes,then closed it,but it came back again !

---

### Post by Najand on 2007-06-08
Edit it using:
```

sudo nano /etc/fstab

```

---

### Post by Drakkor on 2007-06-08
That's what I'm using , Najand , after I hit "Y" is there a special way to exit or something ?

---

### Post by Najand on 2007-06-08
If you ave done it properly, then there is a possiblity that your /dev/sdb1 has been mounted as a read only filesystem. Can you post the output of "mount" command here, too?

---

### Post by Drakkor on 2007-06-08
YAY !! :p I GOT IT !!  After hitting yes to save changes, I was just closing the window, it seems one has to hit 
enter for it to take !!  Anyway that did the trick !  Thanks for bearing with me, Najand !  Cheers :D

---

### Post by Najand on 2007-06-08
It is ok... Did it help?

---

### Post by Drakkor on 2007-06-08
Yep, everything's fine now, problem solved, I was able to delete the folder just fine, Thanks !  :)

---

### Post by Najand on 2007-06-08
Nice, Congrats.

---

