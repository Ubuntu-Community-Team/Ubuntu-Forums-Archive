---
title: "windows MBR overwrite problem???"
date: 2011-07-07
forum: Any Other OS
---

### Post by javajames97 on 2011-07-07
OK, this is mostly a windows question

I have had windows and ubuntu dual booted for most of the time i have had a laptop (irrelevant)

I recently got a virus, i ended up having to reformat everything (losing everything related to ubuntu, which still makes me twitch), and reinstalling it all

now i have another virus (just weeks after the first) and i dont want to lose everything, at least before it was an opportunity to upgrade ubuntu without leaving my machine on for 6 hours. I dont mind reinstalling everything on windows but not on ubuntu. So when i boot into the install disk [pendrive] for windows i find that it quite neatly allows me to install windows to one partition, however, i am worried that i may write over the MBR, which would mean that i couldn't access GRUB, and ubuntu.

I want to know if its possible to completely reinstall windows from the normal install disk without over writing the MBR

thanks, james, the exhausted young enthusiast

---

### Post by javajames97 on 2011-07-07
Dont worry

[http://embraceubuntu.com/2005/10/20/backing-up-the-mbr/]("http://embraceubuntu.com/2005/10/20/backing-up-the-mbr/")

---

### Post by Neoxhadowespio on 2011-07-07
Eheheh. 
Very Simple Tip: *"Don't Panic!"*

---

### Post by oldfred on 2011-07-07
I suggest these links to just reinstall grub2's boot loader to the MBR.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

dd also has a nickname - Data Destroyer. It is a very powerful command and can do great things. But one typo and you can do great damage. Also not knowing what you are copying can be an issue.

Link by javajames97 suggests bs=512. But that includes partition table. If you have made no changes to partition table that will work. But if partition table is different you have just restored the old version which may now be corrupted.

I have often suggest using 446, others say use 440 as the area from 440 to 446 is not used by Linux.
Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
dd if=/dev/sda of=/mbr.bin bs=446 count=1
Zero out MBR only of sda Use 440 if windows as serial number is between 440 & 446.
dd if=/dev/zero of=/dev/sda bs=446 count=1

---

