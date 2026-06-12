---
title: "Formatting usb for mac"
date: 2010-01-28
forum: Apple Hardware Users
---

### Post by Kyouya on 2010-01-28
So, I'm taking a computer programing class (Python) and we were given usb drives with Ubuntu on them. Naturally, they're only formatted for windows computers. Press F12, select boot from usb, and Ubuntu comes up easily and painlessly. According to my teacher, there is a way to format the usb drives so they'll work with Macs, but he refuses to tell me how. I want to format it to work with my Mac without erasing all the data on it (since I need it for class). Is there a way to do that?

---

### Post by linuxopjemac on 2010-01-28
I only know a way where you first partition the USB drive, this will mean that you have to delete what's on it...

[http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick](http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick)

---

### Post by alwayshere on 2010-01-28
see this [https://help.ubuntu.com/community/Installation/FromImgFiles]("https://help.ubuntu.com/community/Installation/FromImgFiles") scroll down

---

### Post by Kyouya on 2010-01-28
> **alwayshere said:**
> see this [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles) scroll down
If Ubuntu is already on the usb, where would I get the .img file for it?

---

### Post by alwayshere on 2010-01-28
Just use the iso file  and  usb-creator which you should already have
if not the below command will install it

sudo apt-get install usb-creator
----------------------------------

if ya cant find the launcher put below in terminal to lanunch

usb-creator
---------------------------------

see this how to [https://help.ubuntu.com/community/Installation/FromImgFiles]("https://help.ubuntu.com/community/Installation/FromImgFiles")

---

### Post by Kyouya on 2010-01-28
Forgive any stupid questions (I'm usually pretty good with macs), but is the usb-creator supposed to get the iso file from the usb and then I just go from there? I'm trying to do all of this *on* a mac, btw. Or do I have to load Ubuntu on a windows machine and do it from there?

---

### Post by Megafag on 2010-01-28
> **Kyouya said:**
> Forgive any stupid questions (I'm usually pretty good with macs), but is the usb-creator supposed to get the iso file from the usb and then I just go from there? I'm trying to do all of this *on* a mac, btw. Or do I have to load Ubuntu on a windows machine and do it from there?

Probably the latter. why not just download ubuntu for mac yourself?

---

### Post by Kyouya on 2010-01-28
Because I need it for class. The actual usb has a lot of files that I need in order to complete the assignments and stuff.

---

### Post by Odin Overland on 2010-01-28
Are you just trying to install the the Ubuntu OS off of the USB drive or run the OS off of it?  My guess is that you are having a partition table problem, since your Mac is most likely GPT and the USB is formatted in MBR.  Are you unable to use a CD drive to install the Ubuntu OS?  I just successfully started triple-booting my MacBook without using rEFIt or Bootcamp Assistant (Mac OS 10.6.2, Ubuntu 9.10, and Windows XP).  Can these files on the flash drive just not be accessed after you have Ubuntu installed?  What kind of Mac are you even working off of?

---

### Post by alwayshere on 2010-01-28
Mac OS X

Command Line Interface

   1. Download the desired .img file
   2. Open a Terminal (in /Applications/Utilities/)
   3.

      Run diskutil list to get the current list of devices
   4. Insert your flash media
   5.

      Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)
   6.

      Run diskutil unmountDisk /dev/diskN (replace N with the disk number from the last command; in the previous example, N would be 2)
   7.

      Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img, /dev/rdiskN is faster than /dev/diskN). If you see the error dd: Invalid number `1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
   8.

      Run diskutil eject /dev/diskN and remove your flash media when the command complete

---

### Post by Kyouya on 2010-01-31
When I try to boot from the usb (which has ubuntu on it; I just put it on a different usb drive), it says "Missing Operating System."

---

### Post by alwayshere on 2010-02-02
go to the bios and set it to boot from usb

---

### Post by linuxopjemac on 2010-02-02
alwayshere: we are woring with macs, you can't just go to the BIOS

---

### Post by Kyouya on 2010-02-02
I'm using rEFIt, if that helps any.

---

