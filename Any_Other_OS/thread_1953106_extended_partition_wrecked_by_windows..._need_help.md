---
title: "extended partition wrecked by windows... need help to restore"
date: 2012-04-05
forum: Any Other OS
---

### Post by Loader009 on 2012-04-05
Hey,
I need help (well, who don't).

Windows wrecked my extended partition (which had a few logical volumes) and I don't know how I could restore them O_O

Some information about my System (after partition #2 -> as far as I remember):
1 HDD (sda)
Pr = Primary; Lo = Logical
Pr #1 512MB ext2 /boot (was/is active)
Pr #2 ~64GB NTFS Windows C:
Ex #3
|- Lo #4 ~670GB NTFS Windows Data D: --- vanished (nearly everything was there...)
|- Lo #6 ~128GB NTFS TestPartition E:  (Used for testing bigger things like video editing) --- vanished
|- Lo #7 ~1,5GB Swap --- vanished (?!?)
|- Lo #5 ~80GB ext4 root Linux ---  didn't vanish!?! Using it right now.

This is the order I picked at last afair.


What happened?
I decided to activate the "TESTSIGNING" in order to use FreeOTFE. -> I forgot, that grub was active right now.
So "bcdedit /set TESTSIGNING ON" gave a "bootsector is not in the systemmemory" (in german).
Well, after a few tries I noticed about grub.
After a few reboots I had set the Windows partition -> active
I noticed, suddenly a few partitions disappeared... thought the would come back after reboot. They didn't.
Testsigning is now active, but useless if I can't get back my Data partition.

Grub partition is active again, as you can guess, the logical partitions aren't back.

Maybe some of you have any idea.

I backupped my MBR (in Hex O_ó) to my usb stick.
I have a notebook with Linux (Mint, based on Ubuntu) and windows on it.
Looked over google, the last I was reading is "EBR" (extended boot record) but found no program to modify it.
Greetings

---

### Post by oldfred on 2012-04-05
Testdisk looks for the start & ends of partitions on the drive. So it may find your old partitions. It can be somewhat confusing if you have repartitioned several times as it often finds all the changes and it then can be difficult to know which is correct. You then have to review and make sure you do not try to recover partitions that overlap. Since you have some idea of size that should help, but testdisk uses the old cylinder-head-sector sizes.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
 or download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Testdisk uses CHS - formula for conversion to LBA
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

---

### Post by Loader009 on 2012-04-05
Great thanks!
After about a half an hour after my posting I found "EASEUS Partition Recovery" for windows.
It have found my partitions, but recovers them only as "Primary" Partition.
It's not that bad, I've got my data back.

I will take your links for some other day (tomorrow I think), very useful knowledge :)
Greetings and thanks!


edit: Got it back as before, extended partition with the logical partitions in it.
Minitool Partition Wizard Home Edition... <- should have used it before.
It found all partitions and could convert between logical and primary partitions :D

---

