---
title: "How do I set up permissions to use an external usb hard drive"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by dominicg on 2006-12-11
I have a dual boot set up laptop with XP and edgy and have gradually been working my way through setting up things in ubuntu.  The forums have been a great help by the way!

I have a LaCie external usb hard drive and in XP created a partition with the ext3 file system using Acronis Disk Director. However, I cannot access this in ubuntu as I am told root is the owner.

How do I set it up so I can use this partition?](*,)

---

### Post by bodhi.zazen on 2006-12-11
> **dominicg said:**
> I have a dual boot set up laptop with XP and edgy and have gradually been working my way through setting up things in ubuntu.  The forums have been a great help by the way!

I have a LaCie external usb hard drive and in XP created a partition with the ext3 file system using Acronis Disk Director. However, I cannot access this in ubuntu as I am told root is the owner.

How do I set it up so I can use this partition?](*,)

I assume the USB drive is /dev/sda1 ....

```
sudo mkdir /media/usb
sudo mount /dev/sda1 /media/usb
sudo chown root:users /media/usb
sudo chmod 770 /media/usb
```

You can skip the chown if you like.....

---

### Post by nickburns on 2006-12-11
If you drive mounts by itself you should not have to do the first two steps that bodhi.zazen gave.  You'll only have to:

sudo chown root:users /media/usbdrive
sudo chmod 770 /media/usbdrive

just replace 'usbdrive' with the name that it automounts to.

---

### Post by dominicg on 2006-12-12
I'm afraid that didn't work.  When I first logged in after partitioning the external drive both partitions showed on the Desktop, LACIE (NTFS) and usbdisk (ext3).  After trying the above only the LACIE (NTFS) partition shows up.  The usbdisk partition shows up in the media directory with a cross by it, but I now get the message 'The folder contents cannot be displayed - You do not have permissions to view this folder'.  In properties its location is /media, name usbdisk, owner root.  Any suggestions?

---

### Post by bodhi.zazen on 2006-12-12
post the output of these two commands:

ls -l /media
sudo fdisk -l

---

### Post by dominicg on 2006-12-12
Here is the output of ls -l /media
total 20
lrwxrwxrwx 1 root    root       6 2006-12-09 03:24 cdrom -> cdrom0
drwxr-xr-x 2 root    root    4096 2006-12-09 03:24 cdrom0
dr-x------ 1 dominic dominic 8192 2006-12-06 17:51 LACIE
drwxr-xr-x 2 root    root    4096 2006-12-12 11:17 usb

and sudo fdisk -l
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4008    32194228+   7  HPFS/NTFS
/dev/hda2            4009        7158    25302375   83  Linux
/dev/hda3            7159        7296     1108485    5  Extended
/dev/hda5            7159        7296     1108453+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11110    89241043+   7  HPFS/NTFS
/dev/sda2           11111       19457    67047277+   5  Extended
/dev/sda5           11111       19457    67047246   83  Linux


Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4008    32194228+   7  HPFS/NTFS
/dev/hda2            4009        7158    25302375   83  Linux
/dev/hda3            7159        7296     1108485    5  Extended
/dev/hda5            7159        7296     1108453+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11110    89241043+   7  HPFS/NTFS
/dev/sda2           11111       19457    67047277+   5  Extended
/dev/sda5           11111       19457    67047246   83  Linux

Hope this will be of some help.  Thanks for your help.

---

### Post by bodhi.zazen on 2006-12-12
Thank you.

I assume the partition you want to mount is /dev/sda5 and the mount point is /media/usb.

You can make a different mount point if you like...

With the usb device attached, and the device mounted at /media/usb:

```
sudo chown root:users /media/usb
sudo chown 770 /media/usb
```

If that fails you can fall back to:
```
sudo chmod 777 /media/usb
```

If you are paranoid:
```
sudo chown user_name:user_name /media/usb
sudo chmod 700 /media/usb
```Where user_name is your user name. you likely do not need to sudo that last chmod, but can't hurt !

---

### Post by dominicg on 2006-12-12
Thanks a lot for your help - I now have access to my hard drive!

---

