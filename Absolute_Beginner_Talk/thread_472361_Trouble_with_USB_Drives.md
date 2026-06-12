---
title: "Trouble with USB Drives"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by dehjli on 2007-06-13
I'm really new to ubuntu and linux.  I just installed 7.04 on my old Thinkpad T40 to try it out.  I've already run into a few problems, like getting the scroll to work on the trackpoint, but the biggest problem I've had is using external drives.

I've tried to use two different USB drives and neither one of them seem to mount.  I am not getting an error message, and they aren't showing up on when I look for the in the Computer window.  Both of the drives work fine on my Windows XP machine.  One is NTFS formatted, and the other is Fat32.

I thought something might be wrong with my USB in general, but other devices (like my USB floppy drive) seem to work just fine.  Can someone give some advice on how I can get my USB hard drives to work with ubuntu?

A little more info.  The first drive I tried is just a Dell 2GB USB Flash Drive.  The other drive I tried was a Western Digital Hard Drive, that I put an enclosure over.  The enclosure is somewhat of an off brand, and they linux is not one of the supported operating systems for it, but it's plug-and-play for Windows, so I'm sort of crossing my fingers that it might work for ubuntu?

Any help is appreciated.

---

### Post by cvmostert on 2007-06-13
There are lots of ways.. but first make sure that your T40 sees the usb drives...

> sudo lsusb
or use this to see the partitions and where they are ( in order to mount them later)
> sudo fdisk -l

Then you will see if they are there at all

Normally a internal disk is displayed as /dev/hda1 or something like that 
an external disk is displayed like /dev/sda1 or /dev/sdab1 (not allways)

after finding the external drive try and mount it like this...

1. first make sure you have a place to mount it for example /media/usbdrive
2. then mount the disk by using
> sudo mount /dev/sda1 /media/usbdrive
This is the basics, if you have trouble... it is really easy to get help on the irc channel #ubuntu on the irc.freenode.net server.. 

good luck.. later you can make it mount everytime you boot by putting it in your fstab.. 
be sure to check out the permisions on the drives for you might not be able to write to them
normally NTFS is a problem but it has been known to work.

---

### Post by dehjli on 2007-06-13
I guess my problem is that my computer is not "seeing" either of the drives.  Here is the output from sudo lsusb

```

Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

and from sudo fdisk -l
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4676    37559938+  83  Linux
/dev/sda2            4677        4864     1510110    5  Extended
/dev/sda5            4677        4864     1510078+  82  Linux swap / Solaris

```

Suggestions?

---

### Post by moore.bryan on 2007-06-13
[I]first, are you running gnome or kde?
second, have you installed pmount?  (i can never remember if its already installed or not.)

have you tried to manually mount the usb device when you plug it in?
[/I]

---

### Post by moore.bryan on 2007-06-13
*also, getting linux to recognize ntfs requires some work...*

---

### Post by timcredible on 2007-06-13
keep in mind that laptops typically provide sub-normal levels of power through usb ports in order to keep battery drain to a minimum, so you may have to use the external power source if available on the external hard drive.  also, if the port is usb 1.x and the flash drive is usb 2.0, there are sometimes some issues with that - or the flash drive might not be working due to it being ntfs, just format it fat16 so it's useable by any os.

---

### Post by dehjli on 2007-06-13
I'm using gnome. 

pmount wasn't installed, so I installed it using Synaptics Package Manager.  No Change.

I haven't tried manually mounting it, mainly because I don't know how.

My laptop has USB 2.0 ports.  They worked fine with both of these drives when I had Windows installed.

The flash drive is actually formatted as Fat32, and the USB hard drive is formated as NTFS.

Help???

---

### Post by moore.bryan on 2007-06-13
[I]just to double-check, try installing gnome-volume-manager.
```
sudo aptitude install --with-recommends gnome-volume-manager
```
if it's already installed, that gives us more info; if not, then it might solve your problems.
post after you're done.
;-)
[/I]

---

### Post by Inxsible on 2007-06-13
Did you have your USB drive connected when you did 
```
lsusb
sudo fdisk -l
```
 
When you installed pmount, did you use it to mount your usb drive?
 
Just installing pmount won't do !

---

### Post by Inxsible on 2007-06-13
> **timcredible said:**
> keep in mind that laptops typically provide sub-normal levels of power through usb ports in order to keep battery drain to a minimum, so you may have to use the external power source if available on the external hard drive. also, if the port is usb 1.x and the flash drive is usb 2.0, there are sometimes some issues with that - or the flash drive might not be working due to it being ntfs, just format it fat16 so it's useable by any os.
You can read NTFS formatted drives in Linux without any problems. To achieve write access, you need to install ntfs-3g

---

### Post by dehjli on 2007-06-13
Here's the output from sudo aptitude install --with-recommends gnome-volume-manager

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

I had the usb plugged in when I did  lsusb and sudo fdisk -l

I didn't try mounting with pmount, although I installed it.  Can you explain how I would do this?  Can I mount it if the hard drives aren't even being detected?

---

### Post by moore.bryan on 2007-06-14
[I]that's okay, it meant you already have a volume manager... the downside is it means your manager isn't seeing your usb stuff.  usually, your first usb drive will be sda1, so in a terminal you can try:
```
sudo mkdir /media/usbdrive
pmount /dev/sda1 /media/usbdrive
```
now, all you've done is make a place for pmount to temporarily mount the drive (mkdir=make directory) and told it to mount.
fingers crossed.[/I]

---

### Post by dehjli on 2007-06-14
I created the /media/usbdrive directory, but when I tried to the pmount /dev/sda1 /media/usbdrive
command I got this output:

```

Error: device /dev/sda1 is already mounted to /

```

Here's my sudo fdisk -l again:

```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4676    37559938+  83  Linux
/dev/sda2            4677        4864     1510110    5  Extended
/dev/sda5            4677        4864     1510078+  82  Linux swap / Solaris

```

It definitely appears /dev/sda1 is already mounted.

---

### Post by moore.bryan on 2007-06-14
[I]no problem... my own stupid fault for not reading earlier in your posts.
instead of /dev/sda1 try /dev/sdb1...
[/I]

---

### Post by dehjli on 2007-06-14
Here's the output:

```
Error: device /dev/sdb1 does not exist
```

---

### Post by dehjli on 2007-06-14
I just used my ubuntu cd to boot on a different computer, and it was able to automount the external hard drive that I'm having trouble with.  I'm starting to suspect that my IBM Thinkpad is just having difficulties running ubuntu.  Has anyone else run into a lot of trouble using ubuntu on a Thinkpad?

---

### Post by moore.bryan on 2007-06-15
*unfortunately, i'd have to agree...*

---

### Post by Inxsible on 2007-06-15
First connect your drive and then do this:
Post the results here
```
sudo fdisk -l
```

then
```
pmount /dev/<device name obtained in earlier step> usbdrive
```

you do NOT have to specify the path for the mount point, as pmount always mounts it under /media. Make sure that you do NOT already have the folder called 'usbdrive' since pmount actually creates one for you.

---

### Post by Inxsible on 2007-06-15
i have never had any troubles using hard drives in my T40 or T42

---

### Post by moore.bryan on 2007-06-15
> **Inxsible said:**
> you do NOT have to specify the path for the mount point, as pmount always mounts it under /media. Make sure that you do NOT already have the folder called 'usbdrive' since pmount actually creates one for you.
[i]only suggested because pmount NEVER made the mount-point properly for me...
;-)[/i]

---

### Post by Inxsible on 2007-06-15
> **moore.bryan said:**
> *only suggested because pmount NEVER made the mount-point properly for me...*
*;-)*
 
That's strange, because if i gave the path, it gave me an error saying that I couldnt have / (slash) in my folder name. I do not rbr the exact error.
 
pmount has always worked for me.

---

### Post by glombo on 2007-06-15
Hey. Im pretty new to using linux and very new to ubuntu.
I've tried what has been said trying to mount my Seagate drive.

User Root:
```
mkdir /media/seagate
mount /dev/sdb1 /media/seagate
```

all looked good until...
```
mount: you must specify the filesystem type
```

PLEASE HELP!! ](*,)

---

### Post by moore.bryan on 2007-06-15
[I]when using the mount command, it's looking at your /etc/fstab file for an entry.  try the pmount command.
[/I]

---

### Post by moore.bryan on 2007-06-15
> **Inxsible said:**
> That's strange... pmount has always worked for me.
*yeah, i know... it was a major snafu until i realized what was happening.*

---

