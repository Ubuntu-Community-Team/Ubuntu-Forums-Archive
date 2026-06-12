---
title: "Iomega 250 usb Zip Drive"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by Lopsicle on 2006-10-16
.................................................................................................................................

---

### Post by bodhi.zazen on 2006-10-16
> **Lopsicle said:**
> Can someone please explain how to get my zip drive working, it's Iomega 250 usb.The other threads are at least 2 years old and I thought they must be a simpler way to install by now?

It should work out of the box. You need a mount point and for some reason zip drives are numbered hdx**4**.

Put a zip drive in the disk, open a terminal, and:

```
sudo mkdir /media/zip
sudo fdisk -l
```
The fdisk command will list the zip drive /dev/sd[color=red]x[/color]**4** where x the letter of the drive.

Now```
sudo mount -t vfat /dev/sd[color=red]x[/color]**4** /media/zip
```

Add a line to fstab (/etc/fstab)if needed:```
/dev/sd[color=red]x[/color]**4** /media/zip vfat noauto,users,rw 0 0
```

---

### Post by Lopsicle on 2006-10-16
.............................................................................................

---

### Post by bodhi.zazen on 2006-10-16
Sorry to ask the obvious, but do you have a disk known to work in the drive that is also known to work?

If so, what type of zip 250? USB,internal ?

Otherwise try this: [Zip250](http://doc.gwos.org/index.php/IomegaZip)

I did not need a sym link, perhpaps you do?

---

### Post by Lopsicle on 2006-10-16
.........................................................................................

---

### Post by Lopsicle on 2006-10-16
.................................................................................

---

### Post by Lopsicle on 2006-10-16
.....................................................................................

---

### Post by bodhi.zazen on 2006-10-16
> **Lopsicle said:**
> Yet another question comes to a full stop. Im sure if I hang around long enough one of my questions might get a reply. I wont hold my breath though.

I may not have a zip, right panel numbers, sound in firefox, cd's keep ejecting for who knows what reason.

But WTF I got pretty icons and a spinning desktop :p

Sorry but I'm out of ideas. I have the same drive and it works "out of the box" without any additional configuration.

I am at a loss to explain why you do not see the drive with:
"sudo fdisk -l" other then to say that is a small "L" and not the number 1. :-({|=

Ohters are repoting success, perhpas a hardware failure?

The only other links I am aware of are:

[http://ubuntuforums.org/showthread.php?t=29441](http://ubuntuforums.org/showthread.php?t=29441)
[http://www.ubuntuforums.org/showthread.php?t=165984](http://www.ubuntuforums.org/showthread.php?t=165984)

---

