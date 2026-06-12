---
title: "Cant partition Second Hard drive in NTFS"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-04-23
I have a USB external hard drive that im trying to use as a communication device between my virtual machine and Ubuntu.

Using QTparted or gparted, even with the drive completely deleted (unformatted), I still cannot format in NTFS. My only options are EXT3 and Fat32. If I try to format in Fat32, it gives me an error saying there is a mounted file system. If I try EXT3 (which I cant use because windows wont read it) Gparted Hangs and I have to cancel it.

Any ideas?

---

### Post by RobsterUK on 2007-04-23
If it complaining saying the drive is mounted, you might need to unmount it

```
sudo umount /media/disk
```

the path where its mounted may be different to above but the command is the same

If you have a Ubuntu CD you could try booting from that and formatting it

---

### Post by az on 2007-04-23
Install the ntfsprogs package and you should be able to create an ntfs filesystem on the usb drive.

---

### Post by antoz on 2007-04-23
you could try doing it in Windows, right click on My computer > manage> storage devices that will show all your drives and you can then format, I would only do that though if there is nothing else on there that you want to keep.

---

### Post by GSF1200S on 2007-04-23
> **az said:**
> Install the ntfsprogs package and you should be able to create an ntfs filesystem on the usb drive.

Ok I tried that.. but I dont exactly know how to launch the GUI aspect of this.

Using the terminal, I dont know what utility to use... It wouldnt be as bad to mess with my hard drive, but I dont know how to get to the usb drive from the terminal... unless I linked to the location in Nautilus where it mounted. Thats a command I would to figure out from scratch...

thats a thing I havent thought. I wont ask you to post codes.. ill hound google for hours until I find them..

---

### Post by az on 2007-04-23
> **GSF1200S said:**
> Ok I tried that.. but I dont exactly know how to launch the GUI aspect of this.

Using the terminal, I dont know what utility to use... It wouldnt be as bad to mess with my hard drive, but I dont know how to get to the usb drive from the terminal... unless I linked to the location in Nautilus where it mounted. Thats a command I would to figure out from scratch...

thats a thing I havent thought. I wont ask you to post codes.. ill hound google for hours until I find them..

Gparted and qtparted use ntfsprogs.  Gparted will now give you the option.

---

