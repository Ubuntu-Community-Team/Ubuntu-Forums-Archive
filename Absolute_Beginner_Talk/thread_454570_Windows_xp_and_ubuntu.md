---
title: "Windows xp and ubuntu"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-05-25
Im running ubuntu and im trying to install winxp for gaming. When i put the cd in it says the hardrive is not found please make sure it is setup correctly(something like that). How can i fix it?

---

### Post by Sparkster185 on 2007-05-25
Do you have your entire hard disk partitioned to ext2/3?  If so, Windows can't find it.  You probably need to re-size your partitions and create an ntfs one for XP to use.

Beware though, installing XP after Ubuntu will screw up your GRUB bootloader, so you'll need to repair it.

---

### Post by mojo123 on 2007-05-25
im aware of the grub thing so i just need any of my partions to nfts?

---

### Post by Sparkster185 on 2007-05-25
That I'm not quit sure of.  Since my machines had Windows on them already in the 2nd partition ( the first  being the bootloader), Windows is always in the first available one.  I'm not sure if Windows would be able to find an NTFS partition if it's at the end of the disk.

That's a good question actually.

---

### Post by mojo123 on 2007-05-25
I have a nfts partion but theres a caution sign next to it <!>

---

### Post by kinematic on 2007-05-25
windows doesn't use a boot partition,your thinking of the mbr.
windows also needs to be installed to the first primary partition but you can set up a ntfs partition at the end of a drive to use for storage for example....so yes,it can find a ntfs partition at the end of a drive.

---

### Post by mojo123 on 2007-05-25
sorry im a noob >.<
But how do i do this

---

### Post by kinematic on 2007-05-25
first you have to get windows to recognize your harddrive.
is it by any chance a scsi(sata) drive?
if so there's probably a driver included for it with the motherboard wich you have to put on a floppy.
then you can load the driver during windows setup.

---

### Post by coffeecat on 2007-05-25
> **kinematic said:**
> windows also needs to be installed to the first primary partition 

Not quite accurate. Windows **must** be installed on a primary partition (which in Linux-speak would be hda1, hda2, hda3 or hda4 - or sda1, etc) because only a primary partition can have a set boot flag. On my Sony laptop, from which I'm posting now, Windows C:\ is on hda2, the second primary partition, for reasons best known to Sony. :?

That is why Windows C:\ cannot be installed to a logical partition, because you can't have a boot flag on a logical partition. And that is why Linux **can** happily boot from a logical partition - because Grub doesn't bother with the boot flag.

To install Windows you need to create an NTFS **primary** partition with the boot flag set. I think you can do that with Gparted but I haven't got Gparted installed in the setup I'm posting from so I can't check this for you.

---

### Post by godssiren on 2007-05-25
i have never created one with an NTFS format, but it gives it as an option from what I recall...
should be possible.
'

---

