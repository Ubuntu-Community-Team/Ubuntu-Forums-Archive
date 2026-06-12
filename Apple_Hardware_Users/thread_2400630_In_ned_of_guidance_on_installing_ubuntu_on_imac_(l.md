---
title: "In ned of guidance on installing ubuntu on imac (late 2013)"
date: 2018-09-08
forum: Apple Hardware Users
---

### Post by paulrfontenot on 2018-09-08
I am preparing to install Ubuntu on an external HDD connected to my iMac on the USB port. I need some guidance on where to turn to download all of the necessary Canon MX922 printer, Dymo Twin Turbo 450 label printer,Logitech ergo max trackball, Apple Magic mouse, Wacom tablet, wifi, Bluetooth, DNS servers, Viewsonic **VA2446 Series:monitor**, Asus DVD external DVD drive, Western Digital external HDD, Adata external HDD, etc.

Can someone steer me towards the necessary sites to download all of the drivers necessary to successfully install ubuntu?

Any general guidance would also be appreciated. Are there any known installation issues with Ubuntu onto an iMac?  (Any known accounts of system incompatibility between the two operating systems?)

I read different accounts on the optimum formatting for a hard drive for Ubuntu; I would need for the HDD to be formatted to be compatible with both Mac OS High Sierra (10.13.6) & Ubuntu 18.04 LTS. (or later)

GRAPHICS PACKAGE**NVIDIA GeForce GTX 780M:**


Chipset Model:    NVIDIA GeForce GTX 780M
Type:    GPU
Bus:    PCIe
PCIe Lane Width:    x16
VRAM (Dynamic, Max):    4096 MB
Vendor:    NVIDIA (0x10de)
Device ID:    0x119e
Revision ID:    0x00a2
ROM Revision:    3782
Metal:    Supported, feature set macOS GPUFamily1 v3
SYSTEM RESOURCES:
MEMORY: 
Size:    32 GB
Type:    DDR3

STORAGE: 3TB FUSION HD  (& a Western Digital external HDD, and an Adata 4tb HDD)

---

### Post by howefield on 2018-09-08
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by gsahli on 2018-09-12
All but the two printers are plug n play. (I think) 
For Canon, look here:
[http://software.canon-europe.com/products/0010487.asp](http://software.canon-europe.com/products/0010487.asp)
For Dymo, look:
[https://dymo.custhelp.com/app/answers/detail/a_id/101/~/dymo-drivers-and-downloads#lw_linux](https://dymo.custhelp.com/app/answers/detail/a_id/101/~/dymo-drivers-and-downloads#lw_linux)
AFAIK, the best way is to install linux on an ext4 format drive. The installer will do this for you (but you need to know which drive to put it on - size is probably an easy feature to use to distinguish).
Linux will be able to mount Mac drives. But to see ext4 on Mac, you need additional software on the Mac side:
[http://osxdaily.com/2014/03/20/mount-ext-linux-file-system-mac/](http://osxdaily.com/2014/03/20/mount-ext-linux-file-system-mac/)

---

