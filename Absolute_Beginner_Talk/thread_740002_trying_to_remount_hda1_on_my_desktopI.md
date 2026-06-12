---
title: "trying to remount hda1 on my desktopI"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by harryliddic on 2008-03-30
I have been trying to remount  my hda1 on to my desktop so I could retrieve files and music lost during a crash.I have tried[QUOTE][harry@harry-desktop:~$ sudo mke2fs -j /dev/hda1
[sudo] password for harry:
Sorry, try again.
[sudo] password for harry:
mke2fs 1.40.2 (12-Jul-2007)
Could not stat /dev/hda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
harry@harry-desktop:~$ sudo mke2fs -j /dev/hda1 gksudo gedit /etc/fstab
mke2fs 1.40.2 (12-Jul-2007)
mke2fs: invalid blocks count - gksudo
harry@harry-desktop:~$ /dev/hda1 /media/hda1 ext3 defaults 0 1
bash: /dev/hda1: No such file or directory
harry@harry-desktop:~$ sudo mke2fs -j /dev/hda1 gksudo gedit /etc/fstab /dev/hda1 /media/hda1 ext3 defaults 0 1
mke2fs 1.40.2 (12-Jul-2007)
mke2fs: invalid blocks count - gksudo
harry@harry-desktop:~$ 


/QUOTE] and it obviously didn't work.

---

### Post by spiderbatdad on 2008-03-30
mke2fs is the command to make an ext2 or ext3 filesystem. I believe you are looking for sudo mount -t

---

### Post by odiseo77 on 2008-03-30
Just to clarify, are you trying to mount a partition, or format it? There's a similar command to the one you're introducing and its job is to format partitions, so, if all you want is to mount /dev/hda1, don't use this command, but the ***mount*** command.

---

### Post by harryliddic on 2008-03-30
I tried mount and said It couldn't find device in /etc/fstab and /etc/mstab

---

### Post by bumanie on 2008-03-30
Post  a copy of sudo gedit /etc/fstab and someone may be able to help you to edit it. Also read this [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by Barrucadu on 2008-03-30
Try /dev/sda1. Due to a kernel update, all harddrives use the sdX convention (yes, it confused me too).

---

### Post by odiseo77 on 2008-03-30
Besides posting a copy of your /etc/fstab file, it would be helpful to post the output of:

```
sudo fdisk -l
```
(the last character is a minor  *L*)

---

### Post by harryliddic on 2008-03-30
output of gedit fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=05cd73b0-8103-4e6a-8685-8b494ede9871 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=6AE45588E4555801 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=a5bf7916-dee5-4eb0-b81a-81bec1ee1906 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

reply to sudo fdisk -l

harry@harry-desktop:~$ sudo fdisk -l
[sudo] password for harry:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60466447

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865        9484    37110150   83  Linux
/dev/sda3            9485        9729     1967962+  82  Linux swap / Solaris

Disk /dev/sdb: 1031 MB, 1031306752 bytes
32 heads, 63 sectors/track, 999 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0xedba4c3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         969      976562+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2             970         999       30240   82  Linux swap / Solaris
harry@harry-desktop:~$

---

### Post by harryliddic on 2008-03-30
I tried /dev/sda1 and it seemed to be working until my terminal froze.

---

### Post by bumanie on 2008-03-30
Try 
> sudo mount /media/hda1

---

### Post by harryliddic on 2008-03-30
help me find a way to mount my hda1, i have try evry suggestion and it has failed. someone must know the answer.

---

### Post by Tatty on 2008-03-30
AFAIK this should work:

```
sudo mkdir /media/windrive
sudo mount /dev/sda1 /media/windrive
```

then your NTFS partition should appear at /media/windrive

---

### Post by harryliddic on 2008-03-30
I tried this as a non-root command. It asked for root clearance I switched to root and recieved the following  mount: special device /dev/sha1 does not exist
root@harry-desktop:~#

---

### Post by Tatty on 2008-03-30
> **harryliddic said:**
> I tried this as a non-root command. It asked for root clearance I switched to root and recieved the following  mount: special device /dev/sha1 does not exist
root@harry-desktop:~#

that should be sda not sha

---

### Post by harryliddic on 2008-03-30
I tried the corrected syntax and got a root prompt ihave i been sucessfu and where do I find the the mount?

---

### Post by Tatty on 2008-03-31
go to /media/windrive

---

### Post by harryliddic on 2008-03-31
all this trouble becuse I lost all my music on aramok because it crash. sorry to bother you with such a meniak thing but when i go to aramok I can't seem to find /media/windrive would you know where to look and may your children live 200 years?

---

### Post by harryliddic on 2008-03-31
all i get when i go to windrive is a lost and found file, Is this beyond the scope of our discussion?

---

### Post by Tatty on 2008-03-31
Ok ill just explain what those commands are supposed to do to help you troubleshoot...

sudo mkdir /media/windrive
This will create a new directory called /windrive in the directory /media.  We are going to mount your hard drive here.
You can mount a drive to any folder you want, but the convention is to mount it to /media and i chose windrive because it makes sense.

sudo mount /dev/sda1 /media/windrive
This command will actually mount your ntfs partition to the directory you created with the previous command.  I know that your ntfs partition is located at /dev/sda1 because of the fdisk -l output you posted earlier.

After running these commands you should be able to navigate to /media/windrive and see your windows partition.  I am not sure why you can only see a folder called "lost and found".

---

