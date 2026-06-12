---
title: "How to use a USB removable disk drive?"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by agarwaldvk on 2006-03-04
Hi Everybody

I have to transfer about 5 files to be able to configure my WinModem in Ubuntu.

I am intending to copy these files to my USB removable drive.

Can someone tell me how do I use (mount) this drive so that I can copy these files to a directory under Ubuntu?

Or does it work the same way as a floppy drive?


Best regards


Deepak Agarwal

---

### Post by moberry on 2006-03-04
If you are running gnome, it usually will automount. An icon will appear on your desktop. If for some reason it doesnt you can use the command

mount /dev/sdXX /place/to/mount

for example:

mount /dev/sda1 /mnt

nine times out of ten your usb drive will be sda, unless you have other usb devices plugged in, then sdb, sdc, so on....

---

### Post by teaker1s on 2006-03-04
my usb hard disc mounts in gnome and kde no worries on vfat/fat32 format

---

### Post by oscar on 2006-03-04
With my usb memory stick it is automatically mounted when I connect it, an icon shows up on the desktop and one in the Places menu. I imagine the same thing will happen for you. If you are transferring files to it in linux make sure you unmount it before you remove it or some data may be lost. I think you can unmount it by just right clicking the icon (but I have to check that)

---

### Post by teaker1s on 2006-03-04
right click on panel and select add to panel and select disk mounter

- click mount and unmount and play dvd

---

