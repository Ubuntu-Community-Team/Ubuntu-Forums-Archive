---
title: "Editing the grub to specify a different hd"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by Aberrix on 2006-10-06
I am experiencing the following problem I posted ([link]("http://ubuntuforums.org/showthread.php?t=272136"))

**cliffnotes:** Installed a third hard drive and for some reason its showing it as the first instead of the third (ie: sda1 instead of sda3, my ubuntu install changed from sbd2 to sbd3)

I need to edit my grubb to specify booting/mounting the correct hard drive.

Can someone please tell me how I can do this?, thanks in advance.

---

### Post by PigCorpse on 2006-10-06
In the terminal, type 'sudo nano /etc/fstab'

Then change the hard drive number.

---

### Post by Aberrix on 2006-10-06
> **PigCorpse said:**
> In the terminal, type 'sudo nano /etc/fstab'

Then change the hard drive number.

So, in this I can actually change it to whatever I want it? as in change the new drive to be sda3 instead of sda1?

---

### Post by Aberrix on 2006-10-06
ttt

---

### Post by PigCorpse on 2006-10-06
Well, the hard drive number is determined by the location of the partitions I think. You can't change the actual number, but you can change which number is mounted. So it says something like /dev/sda1 and you change that to /dev/sda3, then reboot.

If this doesn't work, please don't hit, sue, or yell.

---

### Post by bulldog on 2006-10-06
Or you can change the way your devices are atached to your motherboard.

Sata determines the drives by which port they are atached.
So your boot device is port one sda1
The second hdd is on port two and so on.

They are no longer master and slave like the IDE drives.
Each hdd is a master drive and could be set as a bootdevice.

By altering the way they are atached you can change their behavior.

Also you should have an option in your BIOS where you can decide which hdd is your boot device.

---

