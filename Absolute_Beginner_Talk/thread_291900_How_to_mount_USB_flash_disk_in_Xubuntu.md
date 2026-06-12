---
title: "How to mount USB flash disk in Xubuntu??"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by leopard6661 on 2006-11-03
I am a total newbe to linux, I have Xubuntu, I have a PCI card for USB, when I put my flash card it isnt recognized, I understood there is some way to mount it manually using commands, but I dont know how, please help me in a detailed way
thanx

---

### Post by Jussi Kukkonen on 2006-11-03
Follow the instructions here (*"To Mount a FAT32 partition"*-part): [https://help.ubuntu.com/community/MountingWindowsPartitions#head-40b4842b2a3a2f56987675b3fed4e878fcec2dd9](https://help.ubuntu.com/community/MountingWindowsPartitions#head-40b4842b2a3a2f56987675b3fed4e878fcec2dd9)

Before that you need to find out the correct device name (/dev/hda1 in the example), so run 
```
tail -f /var/log/messages
```
and plug in the usb disk. You should see the device name in the output (probably sda or something like it). Post the output here if you can't make sense of it.

---

### Post by 3rdalbum on 2006-11-03
Try performing these commands at the terminal:

```

sudo mkdir /media/usbdisk
sudo apt-get install ivman
```

(you must have the Universe repository activated)

When the installation is finished, make sure your drive is unplugged and run the "ivman" command in the terminal. Now plug in your USB flash drive, and it should hopefully appear under /media/usbdisk.

---

### Post by leopard6661 on 2006-11-03
I followed instruction in Jussi Kukkonen post and in the attached link, I found out the usb was named usb 4-1, but still i found nothing on the folder usb. Moreover, the usb isnt recognized no more by my windows, it says it is malfunction, I dont know what to do, is it the flash , or xubuntu did somthing (e.g. formatted) the flash so it is not recognized
Please help

---

