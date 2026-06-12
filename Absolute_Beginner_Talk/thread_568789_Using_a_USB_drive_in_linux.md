---
title: "Using a USB drive in linux"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by mtn_man on 2007-10-06
I am trying to upload my website files from a usb fd to my server (dapper). When I plug in the device the light starts blinking on the device so I think that it is being read. My command line reads [43152142.550000] sdb: assuming drive cache: write through   

then,

 [43152142.600000] sdb: assuming drive cache: write through   


I think that the device has been mounted (but I am not totally sure) as my fstab file reads:
.
.
.
/dev/fd0    /media/floppy0    auto    rw,user,noauto     0     0

If I cd /media/floppy0 there is nothing there...

I am not sure if it is just the wrong file system - like fat32 or my usb device is not really mounted. Any ideas on how to handle this???

many thanks,

newbie

---

### Post by Maxtorm on 2007-10-06
The usb drive won't show up in your fstab because it's not a permanent mount point. What is the output of the following?
```
ls -al /media
```
Also, ```
mount
``` will show you all of your existing mount points. The usb drive will be listed if it mounted when you inserted it. I believe the default mount point for it is /media/disk.

---

### Post by mtn_man on 2007-10-06
ls -la  /media

...
lrwxrwxrwx 1  root root 6         timestamp         cdrom -> cdrom0
drwxr-xr-x   2 root root 4096   timestamp         cdrom0
lrwxrwxrwx  1 root root 7         timestamp         floppy -> floppy0
drwxr-xr-x   2 root root 4096   timestamp         floppy0


sorry, I have to type the output since I do not have my server online yet...

---

### Post by mtn_man on 2007-10-06
when I type mount I see:

procbususb on /proc/bus/usb type usbfs (rw)

when I cd to that dir I see a devices file and a 001 dir, the 001 dir has 2 files (001, 006) in it that appear to be ?????

---

### Post by Maxtorm on 2007-10-06
I believe the proc/bus line in mount only indicates the USB bus rather than any specific device. I've seen those drive cache errors before and they have not affected my ability to mount the device.

As sdb is apparently the USB device, try this:```
sudo su -
cd /media
mkdir usbdevice
mount -t vfat /dev/sdb /media/usbdevice
```In theory, you should now be able to see the contents of the USB device under /media/usbdevice.

---

### Post by mtn_man on 2007-10-07
> **Maxtorm said:**
> I believe the proc/bus line in mount only indicates the USB bus rather than any specific device. I've seen those drive cache errors before and they have not affected my ability to mount the device.

As sdb is apparently the USB device, try this:```
sudo su -
cd /media
mkdir usbdevice
mount -t vfat /dev/sdb /media/usbdevice
```In theory, you should now be able to see the contents of the USB device under /media/usbdevice.
Thanks for the info...I however still cannot seem to get it to read the drive. I have been looking at the syslog (dmesg) and am getting some errors like:

sd 6:0:0:0: Attached scsi removable disk sdb
...               Attached scsi generic sg2 type 0
usb-storage: device scan complete
FAT: invalid media value(0x00)
VFS: cant find a valid FAT filesystem on the dev sdb

So, I am going to attempt to get this server connected to the internet tomorrow and go from there.

---

### Post by prostar on 2007-10-12
I am having the same problem.  I have a USB to IDE converter (Trendnet TU2-IDSA).  It sees the device as /dev/sdb, but no partitions to mount.  Mounting /dev/sdb only gives the device info, no data.  I think I had this problem with my camera as well, but can't remember the solution.

dmesg reports:
```
[ 2498.029728] usb 6-1: new high speed USB device using ehci_hcd and address 3
[ 2498.163523] usb 6-1: configuration #1 chosen from 1 choice
[ 2498.164023] scsi9 : SCSI emulation for USB Mass Storage devices
[ 2498.164076] usb-storage: device found at 3
[ 2498.164079] usb-storage: waiting for device to settle before scanning
[ 2503.161864] usb-storage: device scan complete
[ 2503.162604] scsi 9:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[ 2503.164008] sd 9:0:0:0: Attached scsi disk sdb
[ 2503.164050] sd 9:0:0:0: Attached scsi generic sg2 type 0
```

---

