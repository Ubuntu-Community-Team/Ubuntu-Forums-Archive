---
title: "[SOLVED] How to mount a USB floppy disk drive?"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by peter1608 on 2008-04-03
I am running Ubuntu 7.10 on a Dell Laptop.  I want to transfer some files from a floppy disk, so I borrowed a USB floppy drive and plugged it in ... and nothing happenned.   I know the drive is ok, as it works on other (Windows) pcs - can I get Ubuntu to recognise it in the same way it recognises a USB memory stick as soon as it is plugged in?

Peter

---

### Post by 3rdalbum on 2008-04-03
You might need to mount it manually.

First, do:

```
sudo fdisk -l
```

That will list all connected drives, and their device file names. Yours should be /dev/sda or something like that. Or, it could be /dev/fd0.

Once you know that, do this command:

```
sudo mkdir /media/floppy
```

That creates the "mount point" for the floppy drive.

Now, the following will mount the floppy drive. Assuming that the device file name is /dev/fd0:

```
sudo mount /dev/fd0 /media/floppy
```

---

### Post by vanadium on 2008-04-03
It should automatically mount. that it does not suggests that the file system needs to be checked. Ubuntu won't auto mount "unclean" drives and the procedure 3rdalbum provided will probably show you an error message indicating the reason.

If you have windows around, it will probably be easiest for you to check the USB in the Windows machine. Under linux, you use the dosfsck command for fat formatted USB's.

---

### Post by peter1608 on 2008-04-03
I tried to run the sudo fdisk -l command, and got a screen full of text about unrecognised partitions.   But then, the drive mounted automatically!  Subsequently I unmounted it, unplugged it and tried again, and this time it all went smoothly.  So it looks like some sort of glitch, possible connected with a specific floppy disk which happened to be in the drive.  Anyhow, it's working now and I have transferred the files I want.

---

