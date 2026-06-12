---
title: "usb disk format"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by lost4now on 2008-02-12
This all started with a new usb disk about  4 hours ago.

I ran the rescue cd and then gparted  next formatted to ext2. 

Now I get an error 15 if the usbdisk is plugged in at bootup 

Unplug the disk and the system boots fine But now I cant find the usb disk 

Also it belongs to root and that wont get it either. 

I have searched and tried about everything I can find helpppppp  pleaseeeee

---

### Post by Moop on 2008-02-12
Are you talking about a external hard drive or a usb flash drive?

I think the flash drives should be fat16. I didn't know the ext2 file system worked on them but I've never tried to change one.

---

### Post by Presto123 on 2008-02-12
Most likely, your bootup is set up to boot off a USB drive first and being in EXT3 format it's not  finding the OS it needs (Or thinks it needs). I would just reformat that USB HD as a FAT32 OR go into your BIOS and move the USB drive to not boot up until after the internal.

If it is a flash drive, do as the person says above. Format it to FAT16.

---

### Post by lost4now on 2008-02-12
Thanks Presto123  that solved part of the problem. I can boot now with the usb drive connected.

---

### Post by Yellow Pasque on 2008-02-12
Boot without the drive. Plug it in. Now run:
```
sudo lshw -C disk
```
Does that find it? (post output if so)

---

### Post by lost4now on 2008-02-12
format changed to fat 32 and everything works great


Thanks

Thanks

Thanks

---

