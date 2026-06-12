---
title: "How to remove grub from MBR of an external USB drive?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-04-21
Hi,

I have major problem burning Feisty Fawn Live CD image on a CD-RW (I don't have any CD-R left). It never works so I decided to try to create a LiveUSB (install LiveCD image on a USB drive) to install Feisty from there. I used this command: 

grub-install --root-directory=/mnt /dev/sda  

where:
sda is my USB disk
/mnt is the mount point for the USB disk

I also couldn't install Feisty with the USB disk so I'd like to remove grub from the MBR of the USB disk. Most threads regarding Grub and MBR concerns the internal harddisk, not an external USB one so I'm not sure how to do this. Any help would be appreciated. Thanks!

---

### Post by louieb on 2007-04-21
I not going to be of much help but I have to ask the question. Why does it matter what is on the mbr of an external drive? I guess you could use the **dd** command to write zeros to it.

---

### Post by kilou on 2007-04-21
The problem is that I'm still trying to make a LiveUSB version of Ubuntu to install Feisty from the USB disk. So I have to boot from the USB disk and each time I do this I get grub followed by an error.

---

### Post by Majiq on 2008-05-12
I don't know if you still have this problem, but here's the answer.

[http://www.tuxation.com/mbr-tricks-with-linux.html](http://www.tuxation.com/mbr-tricks-with-linux.html)

Majiq.

---

