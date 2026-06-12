---
title: "WIn XP dual boot CD Rom doesn't work"
date: 2011-08-05
forum: Any Other OS
---

### Post by Jeaux on 2011-08-05
I had Ubuntu 10.04 installed and used Gparted To resize partition to make room for another partition to hopefully install XP on for a dual boot configuration.  Afterwards everything went to hell, but I was able to use liveCD to upgrade system to 11.04 and it restored access to Ubuntu.  Then I formatted the unallocated space to FAT32.  I've investigated different program on a Vista box that would make a Bootable flash drive to install XP off of...  but all atempts fail to install winXP.  I have access to The "Windows" Partition from ubuntu but have no idea how to install XP on it w/o my CDrom working.  Was thinking that maybe a virtual drive with the win XP iso mounted might do it...   but need some guidance.    any suggestions?

---

### Post by Furball588 on 2011-08-05
> **Jeaux said:**
> Was thinking that maybe a virtual drive with the win XP iso mounted might do it...   but need some guidance.    any suggestions?

Can you boot to a USB device?  Those of us old enough remember doing diskless installs of NT via a dos disk and running winnt from i386.  Windows XP can be installed the same way.  I would wonder if you can start the installation this way using dosbox though.

I suppose you could use virtualbox or vmware, but they you're stuck with either running it in the VM or if you boot from the HD, dealing with drivers  (as taking it out of the VM is just like changing a MB).

---

### Post by Jeaux on 2011-08-05
Yes I can boot from USB in boot menu on Dimension E510

---

### Post by Furball588 on 2011-08-05
Someone may want to check me on this...

sudo dd if=/path/to/winxp.iso of=/dev/device/node bs=1M

I would think the result in the end would be a bootable USB key cloned directly from your ISO of XP

I thought I read somewhere you can do the same with unetbootin (although it's designed use was for linux distros)

---

### Post by Jeaux on 2011-08-05
The problem is that when the bootable USB starts to boot it doesn't give an option for which partition to use.  If I were to install another linux distro to the FAT 32 partition could I then use the iso to install windows over the distro?

---

### Post by Furball588 on 2011-08-05
Do you not get the blue screens of installation?  I guess I'm just confused why you wouldn't get a screen where you can add/remove and format partitions.  

With your question, I don't think so.. :)

---

### Post by Jeaux on 2011-08-05
Yes...  It goes thru Windows setup blue screen and then when it gets to the Starting Windows part of the installation it give error message saying that it would harm my computer and freezes

---

### Post by Jeaux on 2011-08-05
Alternatively, I do have a .vdi of an XP install thru Virtualbox.   Is there a method for transfering that to my newly created FAT32 partition and resize it?  And if so how do I alter the MBR to give option to boot it?

---

### Post by Furball588 on 2011-08-05
> **Jeaux said:**
> Yes...  It goes thru Windows setup blue screen and  then when it gets to the Starting Windows part of the installation it  give error message saying that it would harm my computer and  freezes

Sounds like some sort of custom disk.  Can't help much here as the condition would replicate itself no matter how you'd attempt to get it installed.

> **Jeaux said:**
> Alternatively, I do have a .vdi of an XP install thru Virtualbox.   Is there a method for transfering that to my newly created FAT32 partition and resize it?  And if so how do I alter the MBR to give option to boot it?

Taking it out of the VM is like changing MB... you're stuck with dealing with the driver change and a repair of the OS.  If you can't boot a cd, I'm not sure how you'll run a repair.

---

