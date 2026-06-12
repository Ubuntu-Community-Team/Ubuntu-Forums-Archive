---
title: "Can a XP F32 HD be slaved to Linux?"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by s1baker on 2007-10-09
I am building a Linux setup on a separate HD in my box. I have a lot of txtfiles, .exe's ( just
installed DOSMU dos emulator, and so far it works great ), jpg's, html's etc, on a XP HD
that I have been using as a second backup drive on XP. Now, I have this XP HD
setup as a slave on my Linux HD, but can't get Linux to reconize it. Can it be done?
 The XP HD was formatted as F32, I believe. If it can be done, how can I do it?
Thanks, any help/info appreciated.

---

### Post by jfinkels on 2007-10-09
I don't know what you mean when you ask if a hard disk drive can be "slaved to Linux", but if you have your HDDs plugged in properly and jumpers set appropriately, you should be able to view all installed, readable media using fdisk. Type the following in the terminal to view all disks and partitions:```
sudo fdisk -l
``` If you don't see all your drives, you don't have them plugged in appropriately, or you don't have jumpers set. fdisk will recognize drives regardless of partitions on those drives and filesystems on those partitions.

I prefer using cable select on all ATA/IDE drives whenever possible, it makes my life much easier.

---

### Post by s1baker on 2007-10-10
When I type  sudo fdisk -l I get this:
=========================
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4111    33021576    c  W95 FAT32 (LBA)
=====================================

And when i go to computer and click the icon I get this:

===============================
error: device /dev/hdb1 is not removable

error: could not execute pmount
===========================

The Linux HD is plugged correctly into the connector at the end of the cable  and the XP Fat32 HD is plugged correctly into the middle connector of the ribbon.

---

### Post by jfinkels on 2007-10-10
> **s1baker said:**
> ```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4111    33021576    c  W95 FAT32 (LBA)

```


Alrighty, so the hard disk drive containing your FAT32 partition is called /dev/hdb, and the FAT32 partition itself is called /dev/hdb1.

Make a directory at which to mount it:```
sudo mkdir /mnt/windisk
```
Make sure it is unmounted:```
sudo umount /dev/hdb1
```
Now try to mount it:```
sudo mount /dev/hdb1 /mnt/windisk
```
If this succeeds, you should be able to view the contents of the partition (if any) by doing the following:```
ls /mnt/windisk
```

Let me know how this goes.

Also, could you post the output of the following command? It will let us know if your computer is trying to automatically mount /dev/hdb1:```
cat /etc/fstab
```

---

### Post by s1baker on 2007-10-10
OK, got it mounted and got it to list.

I typed the command "cat /etc/fstab" and got this:

=====================================
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
=============================================

 I went into the computer icon on desktop, and the icon for the HD  shows the name of the HD with this:
31.5 GB Volume:/mnt/windisk.

 I can get a listing of the Windisk files on the HD by clicking into it with
my mouse. Do I need to do anything special at each boot up in order to get
Linux to recognize the  windisk?

---

### Post by jfinkels on 2007-10-10
> **s1baker said:**
> 
 I can get a listing of the Windisk files on the HD by clicking into it with
my mouse. Do I need to do anything special at each boot up in order to get
Linux to recognize the  windisk?

Let me clarify how we access partitions in Linux:

To access files, the partition must be "mounted" somewhere in the root filesystem (i.e. somewhere under the root of the file hierarchy, the "/" directory). You must define a specific directory under which to mount the partition, in this case I directed you to make a directory at /mnt/windisk.  In reality, you can create whatever folder you like, wherever you like (with a few exceptions of course). Ubuntu chooses to put mounted partitions in the "/media/" directory. It really doesn't matter.

Anyway, to have that partition mounted at startup, we can add a line to the file "/etc/fstab". Yours looks like this:```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
```
The first entry in the line is the name of the device, next is the mountpoint (the directory you under which you will find the files contained in the directory), next is the type of the filesystem (the format), next is the options, next is whether or not to backup this file when using the 'dump' utility (doesn't really matter for us), and finally is the order in which you want to check the filesystems. If you want to learn more, go here: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

After creating the directory for your mountpoint, you need to open /etc/fstab using```
gksudo gedit /etc/fstab
``` and add a line to the bottom that looks like this:```

/dev/hdb1 /mnt/windisk vfat defaults 0 2

```
'vfat' is FAT32.

Now test it by typing ```
sudo mount -a
```and then see your files by typing:```
ls /mnt/windisk
```

---

### Post by s1baker on 2007-10-11
Ok, I got it to work except I can't see an icon of the HD in my 'Computer' folder that I have on my desktop. I can get in the HD by going to terminal and typing "gksu nautilus" ( I could not get 'gksudo gedit' to work on my system ) and from the nautilus file browser, I could get into root, and then into the directory /mnt/windisk and from there I could get into the HD and copy files and stuff.  Is there a way to get the icon to display within my 'computer' directory that is on my desktop, so that after boot-up, I could just mouse click into the HD, instead of having to run Nautilus?
 The only things that show in my 'computer' folder on my desktop are "floppy", "CD-RW" and "File System"

---

### Post by jfinkels on 2007-10-11
> **s1baker said:**
> 
 The only things that show in my 'computer' folder on my desktop are "floppy", "CD-RW" and "File System"

I believe this is because your mounted partition is now *in* your "File System"!

To create a launcher on the desktop, right click on the desktop and select "Create Launcher...". Name the launcher whatever you want, but the command to open your partition will be:```
nautilus /mnt/windisk
```You shouldn't need to run nautilus as root to be able to read from this directory, but to check on the permissions of the directory, you can type:```
ls -l /mnt
```If for some reason your launcher fails, you can change the permissions on the directory by doing:```
sudo chown *yourusername*:*yourusername* /mnt/windisk
```As always to learn more about any command, type 'man' followed by the command:```
man chown
man ls
man mkdir
man mount
```

---

### Post by s1baker on 2007-10-11
Thanks Jfinkels, I think that got it. Appreciate the help. I have worked with Windows and DOS for a long time and I know their filing system very well, but what I know about Linux I could write on a postage stamp, but I am learning it bit by bit. Root permissions and Linux ways of doing things are totally new to me.
 I am trying to set up a work station with Ubuntu Linux for my work, and I have absolutely no one to help me except for this forum, which has been a life saver.

---

### Post by jfinkels on 2007-10-11
> **s1baker said:**
> Thanks Jfinkels, I think that got it. Appreciate the help. I have worked with Windows and DOS for a long time and I know their filing system very well, but what I know about Linux I could write on a postage stamp, but I am learning it bit by bit. Root permissions and Linux ways of doing things are totally new to me.
 I am trying to set up a work station with Ubuntu Linux for my work, and I have absolutely no one to help me except for this forum, which has been a life saver.

Glad we could help!

Keep asking questions! :D

---

