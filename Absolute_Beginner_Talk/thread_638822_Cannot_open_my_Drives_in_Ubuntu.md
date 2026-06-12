---
title: "Cannot open my Drives in Ubuntu"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by neomilan on 2007-12-12
My hard drive, originally for windows is refusing to open in ubuntu

I need it to copy my files from my main hardrive to the external

neither are opening.

This is the message:

> 
Cannot mount volume.
Unable to mount the volume.



help!

the hard drive is NTFS

i know there is a problem reading NTFS in linux

if i somehow change it to FAT or the other one... will i lose the files on the drives?

:confused:

---

### Post by meborc on 2007-12-12
well... you need this:```
sudo apt-get install ntfs-config
```this should but a ntfs configuration utility into your menu (the admin. or preferences, IF it is not already there)

start this program to configure the ntfs support

---

### Post by neomilan on 2007-12-12
> **meborc said:**
> well... you need this:```
sudo apt-get install ntfs-config
```this should but a ntfs configuration utility into your menu (the admin. or preferences, IF it is not already there)

start this program to configure the ntfs support

this wont delete any of my files will it?

---

### Post by FuturePilot on 2007-12-12
> **neomilan said:**
> this wont delete any of my files will it?

No it won't. You'll find a Configuration utility under Applications>System Tools after installing it.

---

