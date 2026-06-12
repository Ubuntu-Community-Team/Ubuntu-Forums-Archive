---
title: "boot error"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by kudos1uk on 2007-08-28
Hi,

On booting xubunu 7.04 I get an error during boot:

> meye: unable to power on camera
meye: did you enable the camera in sonypi using the module options?

Been doing lots of reading to try and sort this and understand sonypi is the driver for the sony jogwheel, screen brightness & motioneye camera etc.

I also understand if you have a vaio PCG-C1VN (I do) then I need to set the module option to 1.

> camera:         if you have a PictureBook series Vaio (with the integrated MotionEye camera), set this parameter to 1in order to let the driver access to the camera

But I just can find out how to do this, anyone know?







> **Module options:**
Several options can be passed to the sonypi driver, either by adding them to /etc/modules.conf file, when the driver is compiled as a module or by adding the following to the kernel command line (in your bootloader):
sonypi=minor[[[[,camera],fnkeyinit],verbose],compat]

**minor:** minor number of the misc device /dev/sonypi, default is -1 (automatic allocation, see /proc/misc or kernel logs)
**camera:** if you have a PictureBook series Vaio (with the integrated MotionEye camera), set this parameter to 1in order to let the driver access to the camera
**fnkeyinit:** on some Vaios (C1VE, C1VR etc), the Fn key events don't get enabled unless you set this parameter to 1. Do not use this option unless it's actually necessary, some Vaio models don't deal well with this option. This option is available only if the kernel is compiled without ACPI support (since it conflicts with it and it shouldn't be required anyway if ACPI is already enabled).
**verbose:** print unknown events from the sonypi device
**compat:**         uses some compatibility code for enabling the sonypi events. If the driver worked for you in the past (prior to version 1.5) and does not work anymore, add this option and report to the author.

**Module use:**
In order to automatically load the sonypi module on use, you can put those lines in your /etc/modules.conf file: 
 	alias char-major-10-250 sonypi
 	options sonypi minor=250

This supposes the use of minor 250 for the sonypi device:
 	# mknod /dev/sonypi c 10 250


---

### Post by justleen on 2007-08-28
see if lspci or lsusb can find something..
those command list the usb bus and the pci bus, and will give you quite a bit of info. The make and model is usually listed there as well

# lsusb |grep -i sony
# lsusb |grep - i vaio
# lsusb |grep - i motion
(same with lspci)

---

### Post by kudos1uk on 2007-08-28
> **justleen said:**
> see if lspci or lsusb can find something..
those command list the usb bus and the pci bus, and will give you quite a bit of info. The make and model is usually listed there as well

# lsusb |grep -i sony
# lsusb |grep - i vaio
# lsusb |grep - i motion
(same with lspci)

lspci lists the motioneye camera but I'm not sure how that helps me.

00:0b.0 Multimedia controller: Kawasaki Steel Corporation KL5A72002 Motion JPEG (rev 01)

---

### Post by kudos1uk on 2007-08-29
Sorry to bump this but can anyone help, the motioneye camera should be supported so I don't know why I get this error during boot?

> meye: unable to power on camera
meye: did you enable the camera in sonypi using the module options? 

---

