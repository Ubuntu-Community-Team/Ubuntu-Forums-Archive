---
title: "No GRUB after adding SATA Drive"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by adelodder on 2008-01-06
I have Ubuntu 7.10 and XP installed on a IDE ATA drive.

I added a SATA drive, which I couldn't format to ntfs using GParted.  So I formatted it with Acronis in Windows XP.
[B]
A cursor is blinking at boot.  GRUB does not load.[/B]

I can boot normally when I disable the SATA Primary Drive in the bios.

---

### Post by Dr Small on 2008-01-06
Boot into your BIOS Setup Utility and set the IDE ATA drive to boot before the SATA drive.

---

### Post by daimaru on 2008-01-06
EDIT: nevermind if Dr Smalls answer works, then do not reinstall grub. way too much work if an easy fix like above solves it.

i guess the hd numbers changed so grub is not found anymore on hd0. you have to reinstall grub.
```

sudo grub
root (hd0,?) (? being where your controlling distro is)
setup (hd0)
quit (or exit)

```check your /boot/grub/menu.lst file to find the right number (hd0,?)

---

### Post by adelodder on 2008-01-06
Still not successful.  Thanks for your fast answers.  I tried both suggestions

> 
**Dr. Small:**
Boot into your BIOS Setup Utility and set the IDE ATA drive to boot before the SATA drive.

The machine I am working with is a Dell Dimension 8300 Series with BIOS Version A07 (latest).

In the **Boot Sequence** menu I can only switch between **IDE CD-ROM Device** and **Hard-Disk Drive C:**.  I can enable them and switch the boot sequence.  **No other device is mentioned.**

The **Drive Configuration** menu looks as follow:

SATA Primary Drive       -  Hard Drive - 250 GB
SATA Secondary Drive  -  OFF
Primary Master Drive     -  Hard Drive - 120 GB
Primary Slave Drive       -  Off
Secondary Master Drive-  CD-ROM Device
Secondary Master Drive-  CD-ROM Device
IDE Drive UDMA  -  On

> 
**Daimaru:**
check your /boot/grub/menu.lst file to find the right number (hd0,?)

I booted from the live CD and typed following in a terminal window:

```
sudo grub
```
```
find /boot/grub/stage1
```
which gave me (hd0,3)
```
root (hd0,3)
```
```
setup (hd0)
```
```
quit
```

after rebooting I still get the blinking cursor.  Any fresh suggestions?

---

### Post by adelodder on 2008-01-06
I don't know what to do.  The following thread pointed me out where the problem is: [http://www.techspot.com/vb/topic28605.html]("http://www.techspot.com/vb/topic28605.html")

> 
**from Techspot:**
my Dell Dimension 8300 BIOS (v.A07) lists SATA HDDs before IDE in the configuration, and **the Boot Sequence is TOO basic to set IDE as first boot **- choices are either "BIOS Configuration" or "USB Device".

> 
**from Techspot:**
There is an F12 option at boot to choose the physical drive to boot from  , but will this be required at every startup in order to bypass the SATA drive?

This person placed a modified boot.ini file on his SATA Drive to boot from his IDE drive.  **How can I do so to load GRUB?**

---

