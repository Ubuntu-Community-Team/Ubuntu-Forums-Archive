---
title: "VMWare USB problem"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by funiae on 2008-03-08
Hello,

I don't see usb devices in my Ubuntu running in VMWare. I read some posts about, unfortunately it didn't solve my problem. 
The main problem is that when i'm running:

sudo /etc/init.d/mountdevsubfs.sh start

i got message:

Filesystem type 'usbfs' is not supported. Skipping mount.
ln: creating symbolic link `/dev/bus/usb/devices' to `.usbfs/devices': File exists
mount: mount point /proc/bus/usb does not exist

Additional info:
I have already uncomment lines:
 mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb
I have VMWare tools installed

---

### Post by dcstar on 2008-03-08
> **funiae said:**
> Hello,

I don't see usb devices in my Ubuntu running in VMWare. I read some posts about, unfortunately it didn't solve my problem. 
The main problem is that when i'm running:

sudo /etc/init.d/mountdevsubfs.sh start

i got message:

Filesystem type 'usbfs' is not supported. Skipping mount.
ln: creating symbolic link `/dev/bus/usb/devices' to `.usbfs/devices': File exists
mount: mount point /proc/bus/usb does not exist

Additional info:
I have already uncomment lines:
 mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb
I have VMWare tools installed

Search the Virtualization forum for the solution - and put all VM questions there as well.

---

