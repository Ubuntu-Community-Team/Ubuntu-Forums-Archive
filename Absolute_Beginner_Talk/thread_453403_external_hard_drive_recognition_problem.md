---
title: "external hard drive recognition problem"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by bazzjazz on 2007-05-24
Hi,

I can't find a solution to my problem in the forums so thought I would post and see if someone can assist me.

I have an unused internal hard disk in an external enclosure, USB2, which I want to use as a backup drive.  This works fine in XP with XP automatically recognising the drive when I switch it on and this is how I have done my backups in WIndows.

However, I am in the process of switching to Linux and Dapper won't recognise the drive at all, whether I boot up with it on or whether I swich on when booted.

Here is the output from sudo fdisk -l


Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14334   115137823+  83  Linux
/dev/sda2           14335       14946     4915890    5  Extended
/dev/sda5           14335       14946     4915858+  82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48641   390708801    b  W95 FAT32

Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9335    74983356   83  Linux
/dev/hdb2            9336        9733     3196935    5  Extended
/dev/hdb5            9336        9733     3196903+  82  Linux swap / Solaris

Disk /dev/hdd: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       14595   117234306    7  HPFS/NTFS

Thanks in advance for any help!

regards,

Barry

---

### Post by undertherift on 2007-05-24
I think fdisk is for drives already on your machine (like hard drives).

```
lshw | grep USB
```

or something very similar to that will give you an output of the hardware associated with USB.  Make sure that your device is detected there.  If i got that command wrong, just go ahead and lshw, which should return everything (not just usb).

I'm speaking from having had to do something  similar to mount my iPod.  Oh, then create a directory, and mount the drive. I'll explain that if you need it after you're successful with this.

---

### Post by dstew on 2007-05-24
Are you trying to mount a drive that is present in your fdisk list? If the drive is present in your fdisk list, all you have to do is mount it on your file system. See the mount command man page for instructions (enter man mount in a terminal window).

---

### Post by bazzjazz on 2007-05-24
Hi,

Thanks for the replies.

Here is the contents of  lshw | grep USB

description: USB Controller
          product: CK804 USB Controller
                description: Generic USB device
                description: USB hub
                product: General Purpose USB Hub
                   product: USB Printer
                   description: Generic USB device
                product: USB Wireless Mouse & KeyBoard V1.01
                product: USB-PS/2 Optical Mouse
          description: USB Controller
          product: CK804 USB Controller
                description: USB hub
                description: Generic USB device
                product: USB Scanner
                product: USB Mass Storage Device

The drive is switched on :) but not being picked up, or so it seems....

Dstew, no I'm trying to mount an external drive that is not showing up with fdisk or lshw.

If I install the drive as an internal drive, it works fine, it is just that popping it in an external casing won't seem to work..

regards,

Barry

I just noticed "product: USB Mass Storage Device" as the last item in the list, so I assume this is the drive?  So now, how to mount??

---

### Post by undertherift on 2007-05-24
hmmm that's not the formatted output i was expecting, to be honest.  I wonder if i used a different command (i'll have to check when i get home from work). 

How about checking to see if you have the usb drive module built in?

[http://www.extremetech.com/article2/0,1558,1256766,00.asp](http://www.extremetech.com/article2/0,1558,1256766,00.asp)

I know that says flash, so don't sweat the mounting part. I think there was a way that i found out which bus and then which /dev/sd* it was mounted on.  I can't seem to find the website that i used as a walkthrough.  I'll keep googling.

Edit:: Wait, now we need to mount, i see that listed at the end.  Generally it gets listed as a /dev/sd* item, so we have to figure out which one it is. I don't think it'll be listed with fdisk.

---

### Post by undertherift on 2007-05-24
Found it!

You can follow this pretty closely.  What is the filesystem that you've got?  Fat32?  NTFS?  Its most likely vtfs, in which case, the mount command listed there wont work the same for you. You'll need

mount -t ntfs /dev/sd* /whereveryouremounting

[http://www.novell.com/coolsolutions/feature/11637.html](http://www.novell.com/coolsolutions/feature/11637.html)

---

### Post by bazzjazz on 2007-05-24
Hey,  I got it working..

I did another search on mounting USB mass storage devices and after running 'udevmonitor' and then turning the drive on I was able to see the line:
'UDEV  [1180033834.699147] add@/block/sde/sde1' and once I mounted sde1, I could see everything!

So many thanks for pointing me in the right direction.  Now off to do a belated backup ;)

regards,

Barry

---

### Post by undertherift on 2007-05-24
Congrats, enjoy your new system.

- Vik

---

