---
title: "read write permissions on fat32 external, really need help"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by jude999 on 2007-06-17
Hi all,

I've tried everything I know or found on the forum. I managed to mount my external hard drive and I can see the files on it. But still can't write on it.

It mounts in /home/simon/dd


Output of fdisk -l:
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4687    37648296   83  Linux
/dev/sda2            4688        4864     1421752+   5  Extended
/dev/sda5            4688        4864     1421721   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    b  W95 FAT32

```

What should I try to get write permission?

---

### Post by Happy_Man on 2007-06-17
Put the following command in the terminal:
```
gksudo nautilus
```

And navigate over to /home/simon. Right-click the dd file, choose properties, and edit the permissions so that you and the group with your name have read/write permissions, and so that you are the owner.

---

### Post by jude999 on 2007-06-17
Thanks, just tried that... and I couldn't change the permissions cause the drive is read only!!! stupic computer, that's what I'm trying to change!

Any ideas?

---

### Post by Happy_Man on 2007-06-17
> **jude999 said:**
> Thanks, just tried that... and I couldn't change the permissions cause the drive is read only!!! stupic computer, that's what I'm trying to change!

Any ideas?
Could you please post the output of ```
cat /etc/fstab
```

---

### Post by jude999 on 2007-06-17
the /dev/sdb1 line as edited by me, but it obviously does not work. I tried several options...

```
simon@simon:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=56c1c45c-9273-4336-9d8b-f50f1038e55a / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=fc9095fd-e1c2-4797-b00d-6190d647926b none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hde1       /home/simon/cf  vfat    user,rw,noauto  0       0
/dev/hdb1       /home/media/psp vfat    user,rw,noauto  0       0
/dev/sdb1       /home/simon/dd  vfat    user,rw,noauto  0       0

```

---

### Post by smoker on 2007-06-17
try this:
> sudo chown -R simon:simon /home/simon/dd

---

### Post by jude999 on 2007-06-17
Thanks. Nothing changed, still can't create or delete files: it still says read-only disk.

Anything else?

---

### Post by schorsch on 2007-06-17
> **jude999 said:**
> the /dev/sdb1 line as edited by me, but it obviously does not work. I tried several options...

```
simon@simon:~$ cat /etc/fstab
/dev/sdb1       /home/simon/dd  vfat    user,rw,noauto  0       0

```

You should change the part "user,rw,noauto" to

```
defaults,utf8,umask=022,gid=XXX,uid=YYY
```

whith XXX="your gid" and YYY="your uid" as returned from the "id" command.

Then do 

```

sudo umount /dev/sdb1
sudo mount /dev/sdb1
```

... that should do the trick.

---

### Post by octathlon on 2007-06-18
What schorsch said should work.  

If for some reason it doesn't, you could try umask=000, which works for me. It basically gives full permission to everyone.  This is the line for my vfat partition in my fstab:

```
/dev/hdb9       /mnt/share      vfat    iocharset=utf8,umask=000        0      0
```

---

### Post by Anonii on 2007-06-19
> **schorsch said:**
> You should change the part "user,rw,noauto" to

```
defaults,utf8,umask=022,gid=XXX,uid=YYY
```

whith XXX="your gid" and YYY="your uid" as returned from the "id" command.

Then do 

```

sudo umount /dev/sdb1
sudo mount /dev/sdb1
```

... that should do the trick.
That did it, for me. Thanks.

---

### Post by jude999 on 2007-06-30
(sorry for the delay in answering this)

Just tried the last tip, did not work I stall have no write permissions on my external HD.

Anything else I should try?

---

