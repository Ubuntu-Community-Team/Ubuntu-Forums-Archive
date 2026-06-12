---
title: "[SOLVED] Fdisk for ubuntu"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-11
Is there a program in ubuntu to zap a drive back to blank including the MBR.
I used grub and its stuck on the drive and the windows util's won't clear it.

---

### Post by ciscosurfer on 2006-12-12
There are many utilities for this purpose.  I would suggest using a graphical front-end to parted (GParted).  I would recommend burning the Live GParted ISO to a disc and then rebooting.  From there, you can delete, create, resize, etc. your partitions to your hearts content

Here's the link to the live CD: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by louieb on 2006-12-12
> **ciscosurfer said:**
> There are many utilities for this purpose.  I would suggest using a graphical front-end to parted (GParted). 
I agree with using GParted. There are cfdisk and fidsk (not the same as fdisk for DOS) available.

---

### Post by xyz on 2006-12-12
Gparted's really good!
You may also want to take a look at this:
[Darik's Boot and Nuke]("http://dban.sourceforge.net/")

---

### Post by John E on 2006-12-12
> **squrl said:**
> I used grub and its stuck on the drive and the windows util's won't clear it.

If you're running XP you can clear it using the XP install disk. Boot up into 'Recovery Mode', then type 'fixmbr' to remove Grub. You'll lose the ability to boot into Ubuntu though....

---

### Post by ciscosurfer on 2006-12-12
> **xyz said:**
> Gparted's really good!
You may also want to take a look at this:
[Darik's Boot and Nuke]("http://dban.sourceforge.net/")DBAN looks awesome!  I might give it a go sometime!

---

### Post by bodhi.zazen on 2006-12-12
> **ciscosurfer said:**
> DBAN looks awesome!  I might give it a go sometime!

It is....

---

### Post by nixclusive on 2006-12-12
> **squrl said:**
> Is there a program in ubuntu to zap a drive back to blank including the MBR.
I used grub and its stuck on the drive and the windows util's won't clear it.
Zap a whole disk eh? here's a simple command:

```
dd if=/dev/zero of=/dev/hd? bs=64k count=1600
``` where '?' is the target drive. That would clear the first 100MB off that drive. ;-)

---

### Post by indytim on 2006-12-12
As mentioned in a previous post, GParted Live for a fast solution.  If you want to wipe it totally clean (as in manufacturer's ship state) do a low level format (takes time depending upon the size of the HD).

IndyTim

---

