---
title: "2 linux item"
date: 2009-04-16
forum: Apple Hardware Users
---

### Post by saarakura on 2009-04-16
Hi people... i have a macbook 1.1 with hd 80gb, 30gb to macos x named LEOPARD, 35gb to windows, and 10gb to ubuntu...
but on refit menu appears mac os x from LEOPARD, linux from LEOPARD ( this doesnt work.. appear "erro loading operation system"), linux from ( doont apper nothing.. but works! its enter on grub and i select ubuntu and works fine,and the last windows from partition 4.
my question;... how can i remove the linux item that doesnt work.. ?


thanks

---

### Post by Daisuke_Aramaki on 2009-04-16
> **saarakura said:**
> Hi people... i have a macbook 1.1 with hd 80gb, 30gb to macos x named LEOPARD, 35gb to windows, and 10gb to ubuntu...
but on refit menu appears mac os x from LEOPARD, linux from LEOPARD ( this doesnt work.. appear "erro loading operation system"), linux from ( doont apper nothing.. but works! its enter on grub and i select ubuntu and works fine,and the last windows from partition 4.
my question;... how can i remove the linux item that doesnt work.. ?


thanks


Ok, so you have a Mac partition, a Windows Partition, and Linux partition, is that right? And I assume grub is your bootloader, is that also correct? 

So from what I understand you have four entries on your grub menu list. But I don't really get the Linux from Leopard part. So if you want to get rid of that entry, you can probably do this

The menu.lst file should reside in /boot/grub/menu.lst To make is easier to edit, if you dont want to do it in the command line, just issue this command:

```
sudo gedit /boot/grub/menu.lst
```

I am assuming you have gedit.

Once it is done, just look for the Linux Leopard part. Just comment that part out. Adding # at the beginning of a line will comment that part out. Just be careful that you comment out only the part relevant to the Linux Leopard part. Then when you reboot, this option will not be there in your grub anymore.

Hope that helps. Anyway are you from Japan? Hajimamashite!

---

### Post by saarakura on 2009-04-16
On grub its ok, this duplicate linux appear on refit menu =/

---

### Post by cyberdork33 on 2009-04-17
If it works, I wouldn't recommend messing with it, but you can try this:
[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

---

### Post by saarakura on 2009-04-17
Dont work.. here is the partition table 


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     63062055  Mac OS X HFS+
 3       63324200     84033575  Basic Data
 4       84297728    156301311  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     63062055  af  Mac OS X HFS+
 3 *     63324200     84033575  0c  FAT32 (LBA)
 4       84297728    156301311  07  NTFS/HPFS

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: GRUB
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 63324200:
 Boot Code: GRUB
 File System: FAT32
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 0c  FAT32 (LBA), active

Partition at LBA 84297728:
 Boot Code: Windows NTLDR
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 07  NTFS/HPFS

---

### Post by cyberdork33 on 2009-04-17
it appears you have grub installed to both partition 2 and partition 3. that is a different issue altogether, and there probably something similar you could do to fix it, but I do not have the expertise to figure it out.

---

### Post by saarakura on 2009-04-17
=/ i dont know how to remove too... i will wait for help thanks for attention :D


plz people... no one ? i really dont know what to do =/

---

