---
title: "After upgrading to 6.10 one of my HD disappeared"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by CrucialTK on 2007-03-30
I have a 160 gig HD in my computer, and couldn't get it to mount. I knew I wanted to upgrade to 6.10, so I went ahead and did it. 

I restart the computer, and Ubuntu is no longer recognizing the drive as being there, let alone allowing it to mount. 

What are some possible ways to get it to mount so I can reformat it? Thanks for any and all help!

---

### Post by Adramelech on 2007-03-30
Check if Gparted can see it.
try to mount the Hd.
if he harddisk mounts, the problem is in your fstab file.

---

### Post by taurus on 2007-03-30
Post the output of these two commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l 
cat /etc/fstab
```

---

### Post by CrucialTK on 2007-03-30
> **taurus said:**
> Post the output of these two commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l 
cat /etc/fstab
```

for **sudo fdisk -l**:
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9589    77023611   83  Linux
/dev/hda2            9590        9729     1124550    5  Extended
/dev/hda5            9590        9729     1124518+  82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19457   156288321    7  HPFS/NTFS


for **cat /etc/fstab**:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=34c99272-bbe1-413c-adc4-4ee1cda862e6 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=61d96dd0-6ff8-45b0-8271-5e675f25180f none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2007-03-30
So you want to mount /dev/hdb1--ntfs.

From a terminal, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Now, create a new mount for it and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by CrucialTK on 2007-03-30
Thanks, that def. helped to mount it. Now, is it possible to format it as a 150 gig FAT32 drive? I know my 160 (150) gig Porty is always read as a Fat32 when its plugged in. I want to be able to use this hard drive as read and write, not just read. Linux is the only OS i have on the PC now, so I wanna utilize as much as possible.

---

