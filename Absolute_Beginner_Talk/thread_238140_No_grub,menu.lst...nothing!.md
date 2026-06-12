---
title: "No grub,menu.lst...nothing!"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-08-17
Hi everyone,

I'm on Knoppix right now!
My HD broke down,so I got a new 80G HD (2.5" 80G 5K100 ATA 100 5400t. 8MB)
-first I installed XP Home and then Dapper using the alternate CD
and resized the NTFS partition, created one for Ubuntu+swap and a FAT 32 partion as you can see below.

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+   7  HPFS/NTFS
/dev/hda2            1217        2432     9767520   83  Linux
/dev/hda3            2433        9729    58613152+   5  Extended
/dev/hda5            2557        9729    57617122+   b  W95 FAT32
/dev/hda6            2433        2555      987934+  82  Linux swap / Solaris

When I power on, I've got no grub,so Windows simply starts up. Using Knoppix, I checked my boot file and
found no grub, no menu.lst! Unfortunately I had to leave home as the install was nearing the end. When I
came back, I found a black screen with 2 small white rectagles on it. I powered off and back on and, like I said
before, Windows just started up.
Any help would be much appreciated.

---

### Post by taurus on 2006-08-17
Well, did you remember to install GRUB on MBR during the installing process???

---

### Post by wieman01 on 2006-08-17
You will have to reinstall GRUB if you have a new HDD. Run the LiveCD and configure it:
> sudo grub
Useful link:

[http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation]("http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation")

---

### Post by xyz on 2006-08-17
Thanks guys!
Holy smoke...I don't think I remembered to reinstall GRUB on MBR!
It's the very first time I have a brand-new HD and I totally forgot about that.
I'll check out the restore GRUB link and let you know.

---

### Post by xyz on 2006-08-22
For some odd reasons, none of the solutions worked. I tried just about eveything!!
So I used Maxtor to wipe it all off; Gparted Boot CD to partition and proceeded to install XP Home. My Dapper Alternate wouldn't install proper so I got my old Breezy Install CD and that did it.
Then I did a find/replace Breezy with Dapper in sources.lists and the usual
sudo apt-get update
sudo apt-get distr upgrade
I'm now on Dapper...finally!  :) 
Thanks again for the help. Bye.

PS: By the way, anyone knows how to change to Dapper in my UserCP?
    Just can't figure it, doesn't seem to be in the same place as when
    we upgraded to Breezy!

---

### Post by zxee on 2006-08-22
> **xyz said:**
> 

PS: By the way, anyone knows how to change to Dapper in my UserCP?
    Just can't figure it, doesn't seem to be in the same place as when
    we upgraded to Breezy!
In your CP go to edit profile it's about 2/3 of the way down the form in a drop down menu type selection.

---

