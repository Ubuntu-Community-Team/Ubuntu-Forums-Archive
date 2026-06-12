---
title: "USB Boot CD --&gt; For booting Mac from Live USB"
date: 2011-12-30
forum: Apple Hardware Users
---

### Post by windfix on 2011-12-30
This post on pendrivelinux.com details how to do it for 9.10 and 10.04

[http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/](http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/)

Is anyone able to modify this for use with 11.10?  I have been unable.

I need this for a graduate class I am teaching on F/OSS in Education, and I want my Mac-using students to be able to do what their PC-using classmates can do... namely get introduced to using Ubuntu 11.10 without touching their hard drives.

---

### Post by 2F4U on 2011-12-30
Wouldn't it be easier to use the existing liveCD and boot from that? At least this works in most cases.

---

### Post by windfix on 2011-12-30
That would work, except it's too slow as an alternative to live usb (which can work as a pretty fast operating environment)

---

### Post by phillat5dock on 2012-01-01
> **windfix said:**
> This post on pendrivelinux.com details how to do it for 9.10 and 10.04

[http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/](http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/)

Is anyone able to modify this for use with 11.10?  I have been unable.

I need this for a graduate class I am teaching on F/OSS in Education, and I want my Mac-using students to be able to do what their PC-using classmates can do... namely get introduced to using Ubuntu 11.10 without touching their hard drives.

I have searched the net looking for a way to do this and tried lots and lots of times with absolutely no success at all. At least the Live CD works!

---

### Post by windfix on 2012-01-01
Yes, the method described at pendrivelinux does work, however, for 10.04.  

I too have scoured for a method that works, and that's the only one that does.  Seems like someone who understands the method could update it:  

"The USB Boot CD you create via this tutorial will contain the USB drivers necessary to open a USB connection. GRUB is used to launch initrd (Initial Ram Filesystem) from the CD.  The Initial Ram Filesystem then locates the squash filesystem and persistent casper-rw persistence block file on the USB device and proceeds to boot the Live USB Persistent environment."

I did put in a request on the pendrivelinux contact form... maybe you can too.

---

### Post by fdrake on 2012-01-01
this should do it : [http://www.plop.at/en/bootmanagerdl.html](http://www.plop.at/en/bootmanagerdl.html)

unzip > burn the iso inside the folder into a cd >  plug the live-usb-disk and insert the boot-cd into the computer > when you start up the computer from the disk it will bring you a menu to choose wich device to boot from (usb/hdd/cdrom/etc)>select usb

hope this works for the mac too, since i don't have one I cannot not test it but I did test it on pc that don't boot from usb and it works fine.

---

### Post by windfix on 2012-01-01
fdrake, Thanks!!

This totally works.  I am replying from a MacBook Pro running 11.10 off of USB.  This will save me so many headaches while introducing students to F/OSS... they can all use their own laptops, run from USB, and I'll never need to touch their hard drives - even the Mac users.

Thread solved!  ;)

---

