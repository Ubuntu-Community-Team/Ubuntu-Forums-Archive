---
title: "External Hard Drive Question"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by pjmaggitti on 2007-02-16
Can anyone tell me how to get Ubuntu 6.10 to recognize my Acom Data external hard drive?

Thanks in advance.

---

### Post by petit.padavoine on 2007-02-17
Have you tried mounting it? It should be mounted automatically but you may have to do it manually.
The device will be /dev/hd(a letter)1. If you have one internal drive, the letter will be b, as your first drive is dev/hda. If you have two, it will be c, etc... Mount it to /mnt/hd(a letter)1, or /media/hd(a letter)1.
To mount it, it has to have been formatted. If not, format it with the ext3 filesystem, or FAT32 if both Linux and Windows will need access to it.

---

### Post by pjmaggitti on 2007-02-17
Thank you for that information. Now, where in Ubuntu 6.10 do I insert that bit of code? I'm guessing it's in terminal, but I'm not familiar with how to use it. And do I use /mnt/hdb1 or 
/media/hdb1?

---

### Post by bulldog on 2007-02-17
If you do a ```
sudo fdisk -l (l as in like)
``` with the external drive connected,you get all the information you need. [in a terminal]

You can see what the hdd is called and which partition you want to mount.

---

### Post by pjmaggitti on 2007-02-17
With the external hard drive connected, what I see when I open terminal is

pjm@pjm-desktop:~$

I'm afraid being just one-day new to Ubuntu, this doesn't tell me much. Any further help would be greatly appreciated.

---

### Post by jawwad on 2007-02-17
if you have external one with usb
i think it's plug and play

thank you 

and welcome

---

### Post by pjmaggitti on 2007-02-17
After entering sudo fdisk-l and supplying my password, I got sudo: fdisk-l: command not found.

---

### Post by Spike-X on 2007-02-17
You need to put a space between fdisk and -l

---

### Post by pjmaggitti on 2007-02-17
Thanks. I did, and this is what I got

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30048   241360528+  83  Linux
/dev/sda2           30049       30401     2835472+   5  Extended
/dev/sda5           30049       30401     2835441   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
pjm@pjm-desktop:~$ 

It's the 80.0 GB drive that I need to mount, or is it already mounted and I'm just too much of a newbie to know where to find it?

---

### Post by Spike-X on 2007-02-17
No, if it was mounted, you'd be able to see it.

---

### Post by pjmaggitti on 2007-02-17
OK. So what do I do to be able to see it? I tried the /mnt/hdb1 and /media/hdb1 commands, but here's what I got

pjm@pjm-desktop:~$ /mnt/hbd1
bash: /mnt/hbd1: No such file or directory
pjm@pjm-desktop:~$ /media/hbd1
bash: /media/hbd1: No such file or directory

Do I have the right commands?

Thank you for your patience here.

---

### Post by Spike-X on 2007-02-17
ok, let's see...

First,

```
sudo mkdir /mnt/sdb1
```

This will creat the directory you're trying to mount the drive into.

What kind of file system is the drive? (ie FAT32, ntfs)

---

### Post by pjmaggitti on 2007-02-17
I'm not sure whether the external hard drive is fat32 or ntfs.

Now that I've created the directory into which I want to mount the external drive, what do I do next? And when I'm finally successful, will an icon for that drive appear on my desktop?

---

### Post by Spike-X on 2007-02-17
> **pjmaggitti said:**
> I'm not sure whether the external hard drive is fat32 or ntfs.

Launch Gparted (System > Administration > GNOME Partition Editor) and have a look there, it will tell you.

> **pjmaggitti said:**
> Now that I've created the directory into which I want to mount the external drive, what do I do next? 

You'll need to edit your fstab file:

```
gksudo gedit /etc/fstab
```

Add the following line:

/dev/sdb1     /mnt/sdb1    ntfs-3g       defaults,locale=en_US.utf8       0       0
(assuming it's a ntfs drive and you have ntfs-3g installed - if not, you'll need to install that first through Synaptic)

If it's a FAT32 drive:
/dev/sdb1     /mnt/sdb1    FAT32       defaults,locale=en_US.utf8       0       0
(I think that'll work - I've not tried to mount a FAT32 drive)

You might wanna search the forums for "mount second hard drive" or similar, just to double check this.

After you've added one of the above lines, Save and close, then restart. Hopefully your second drive will be mounted ready to use!



> **pjmaggitti said:**
> And when I'm finally successful, will an icon for that drive appear on my desktop?

Yes.

---

### Post by pjmaggitti on 2007-02-17
pjm@pjm-desktop:~$ gksudo gedit /etc/fstab

(gedit:1077): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Then I got the following popup box

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4aa98e05-56ab-4514-b690-5bc6428e7eff /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=cbe74ca0-f7c3-4e2e-aaca-07e407d801b4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

I'll be away from the computer for about an hour. I'll check for a reply when I get back.

---

### Post by Spike-X on 2007-02-17
> **pjmaggitti said:**
> pjm@pjm-desktop:~$ gksudo gedit /etc/fstab

(gedit:1077): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Dunno what that warning is about, I always get it as well. *shrug*

> **pjmaggitti said:**
> Then I got the following popup box

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4aa98e05-56ab-4514-b690-5bc6428e7eff /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=cbe74ca0-f7c3-4e2e-aaca-07e407d801b4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0


Okay, this is your fstab file, opened in gedit (text editor program) and ready to be edited. Add one of the lines I gave you above (depending on whether the drive is ntfs or FAT32), Save and close, and restart Ubuntu.

> **pjmaggitti said:**
> I'll be away from the computer for about an hour. I'll check for a reply when I get back.

I'll be in bed by then, but I'm sure some other folks will be around to help you out if you're still having problems. Good luck!

---

### Post by jure1873 on 2007-02-17
From the fdisk -l output it seems there are no partitions on that drive, so you'd first need to create a partition on it (fat32 or ntfs, if you use it in win and lin choose fat32, if you need only to access it from linux use ext3). As suggested start up gparted and create a partition on that drive (sdb) and format it, when you do this you'll get /dev/sdb1 available, then it's probably the easiest to unplug it and plug it in again and it'll get recognized automatically, don't mess around with sda in gparted because you could delete your existing data on your internal hard disk.

---

