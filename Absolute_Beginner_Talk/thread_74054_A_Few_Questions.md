---
title: "A Few Questions"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by jamez15 on 2005-10-10
Hey,

I'm new wo Ubuntu and I have two questions:

1. How do you mount a USB flash thumb drive so you can read/write to it?

2. Is there a way to mount a Windows NTFS partition so that you can read/write to it. I've already mounted my NFTS partition using the guide from the Ubuntu, but I can only read not write. I don't want to create a FAT partition to have the ability to read/write.

Thanks in advance,
James

---

### Post by Leif on 2005-10-10
for ntfs, the free option is captive ntfs, which is said to cause problems which can wipe your drive, and paragon, which is not free. search the forums for them for more info

---

### Post by poofyhairguy on 2005-10-10
[QUOTE=jamez15]Hey,

I'm new wo Ubuntu and I have two questions:

1. How do you mount a USB flash thumb drive so you can read/write to it?
[/QUOTE]

Unless its an NTFS drive, just plug it in.

---

### Post by Ampersand on 2005-10-10
A USB drive should be detected and mounted automatically, if you're using Gnome or KDE.

If it's not, you can mount it manually. Firstly, create a directory for it (you only need to do this the first time), for example:

```
sudo mkdir /media/usb 
```

Then to mount, use the command

```
sudo mount -t vfat /dev/sda1 /media/usb 
```.

The drive might be assigned something other than /dev/sda1. The location should be mentioned if you run 

```
 dmesg | tail 
```

a few seconds after connecting it.

---

