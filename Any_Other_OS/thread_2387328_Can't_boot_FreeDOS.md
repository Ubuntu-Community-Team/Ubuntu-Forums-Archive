---
title: "Can't boot FreeDOS"
date: 2018-03-17
forum: Any Other OS
---

### Post by donsy on 2018-03-17
I made a bootable CD with the latest version of FreeDOS, however when I try to boot all I get is a screen with the word FreeDOS immediately followed by a blinking cursor. Everything I try to do after that is unresponsive. My goal is to flash the bios using a Windows executable.

These are the commands I used to create the CD:
```
genisoimage -o bootcd.iso -b FDOEM.144 FDOEM.144
wodim -v bootcd.iso
```

---

### Post by Frogs Hair on 2018-03-17
Moved to Any Other OS.

---

### Post by mörgæs on 2018-03-18
Does the CD work when booted in another computer?

---

### Post by donsy on 2018-03-20
> **mörgæs said:**
> Does the CD work when booted in another computer?

No, but here's what I did to get it to work:

From [http://www.freedos.org/download/](http://www.freedos.org/download/) I downloaded the CDROM "standard" installer (FD12CD.iso), then I used Xfburn to burn it to a CD.

After I boot the CD I choose install, then the language, but then choose the "No, return to DOS" option when asked if I want to install.

My hard drive is still MBR and I have a primary partition formatted VFAT, label type "c" ( W95 FAT32 (LBA) ), so when I change the drive to C: I can access any files located there.

---

