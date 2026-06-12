---
title: "Mounting"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by TurntableJunky-Xx on 2007-05-08
How do I mount a cd drive in ubuntu?

---

### Post by ubnewbie2 on 2007-05-08
put a cd in it, it should mount automatically

---

### Post by TurntableJunky-Xx on 2007-05-08
it doesnt

---

### Post by ubnewbie2 on 2007-05-08
As long as it was a valid data cd, not blank or something weird, then it should have worked, however,

open up a terminal and type

cat /etc/fstab

and one of the lines displayed will be about the cdrom (it will probably mention /media/cdrom0 on the line somewhere. 

 then type something like

sudo mount /dev/hdc

changing hdc to whatever that line showed you as the device name (should be at the start of the line)

---

### Post by TurntableJunky-Xx on 2007-05-08
that didnt work it just says wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by ubnewbie2 on 2007-05-08
Either something is wrong with the drive, or the disc inside it, or the entry in fstab is wrong.

---

### Post by drowner on 2007-05-08
could you post the info in your fstab file?

---

### Post by thewizard5001 on 2007-05-09
Maybe this will help: go to System > Preferences > Removable Drives and Media, and, under "Removable Storage", check atleast the top two checkboxes when it comes up, the rest are optional. These instructions are for Ubuntu 7.04, aka, Ubuntu Feisty, so if you are using Ubuntu 6.10, aka, Ubuntu Edgy, some modifications may be necessary.

---

### Post by fakie_flip on 2007-05-09
maybe your cdrom or dvd rom is bad. what do you get from "dmesg | tail"?

---

### Post by TurntableJunky-Xx on 2007-05-09
[   29.188000] Bluetooth: RFCOMM TTY layer initialized
[   29.188000] Bluetooth: RFCOMM ver 1.8
[   40.160000] eth1: no IPv6 routers present
[ 2142.528000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[ 2142.528000] NTFS-fs warning (device hda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[ 2142.640000] NTFS volume version 3.1.
[ 4541.188000] UDF-fs: No partition found (1)
[ 4541.308000] Unable to identify CD-ROM format.
[ 6234.672000] UDF-fs: No partition found (1)
[ 6234.688000] Unable to identify CD-ROM format.

---

### Post by fakie_flip on 2007-05-09
try putting other cds in it. do they work?

---

