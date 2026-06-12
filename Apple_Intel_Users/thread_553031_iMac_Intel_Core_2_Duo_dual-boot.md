---
title: "iMac Intel Core 2 Duo dual-boot"
date: 2007-09-17
forum: Apple Intel Users
---

### Post by liberalist on 2007-09-17
Hi, I know I can look to other posts and other articles on the net regarding this issue. However, I do not find a good enough answer. On my iMac Intel Core 2 Duo (17-inch, 2.0 GHz processor, 1 GB 667 MHz DDR2 SDRAM), it already went wrong several times. I wish to create a dual-boot (Mac OS X 10.4.10 Tiger and Ubuntu 6.06 or 7.04), but I still don't know how...

That's why I here have an overview of my partitions (the third one being 'free space'), produced by the Partition Inspector of rEFIt. Thank you very much in advance for a possible solution to my problem. 

PS: I know that I need to back-up my work prior to doing this, of course. 

> *** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     52576295  Mac OS X HFS+
 4       95043624    312319623  Mac OS X HFS+

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    312581807  ee  EFI Protective

MBR contents:
 Boot Code: None

Partition at LBA 40:
 Boot Code: Unknown, but bootable
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+

Partition at LBA 95043624:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X HFS+

---

### Post by pxwpxw on 2007-09-17
**liberalist**

The MBR partition table is not synchronised with the GPT table.
That will probably interfere with ubuntu installation and booting.
You could try to synchronise using the refit Partition utility (gptsync), and post the result.
Can you start Macosx from the Apple graphical chooser as well as from the refit menu?
What is on the 2 HFS+ partitions - which one has macosx system?
Where did you try to install ubuntu, and what failed?

---

### Post by liberalist on 2007-09-17
Hello, comments are inline. However, I might opt for installing Kubuntu, since that is the system I am more familiar with. Although I read that it is possible to install KDE over Ubuntu; does this make my system slower? 

> **pxwpxw said:**
> **liberalist**

The MBR partition table is not synchronised with the GPT table.
I have now synchronized them with the partition tool on the boot menu.

That will probably interfere with ubuntu installation and booting.
You could try to synchronise using the refit Partition utility (gptsync), and post the result.
See below *** Report for internal hard disk ***

Can you start Macosx from the Apple graphical chooser as well as from the refit menu?
I can start Mac OS X from the rEFIt menu, but don't know if I can start it from the Apple graphical chooser (should I hold option?). 

What is on the 2 HFS+ partitions - which one has macosx system?
The one of approx. 25 GB is the one that has Mac OS X, the 19/20 GB is for the Linux system. 

Where did you try to install ubuntu, and what failed?
I tried to install it on the 19 GB volume (ext3) with a 1.5 GB volume dedicated to swap. I have 1 GB RAM, is the swap volume enough? 



*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     52576295  Mac OS X HFS+  (Mac OS X partition)
 3       52576296     91885608  Basic Data         ----- to be a Linux ext3 volume 
 4       95043624    312319623  Mac OS X HFS+ (data partition)
 5       91885609     95043623  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     52576295  af  Mac OS X HFS+
 3 *     52576296     91885608  0b  FAT32 (CHS)
 4       95043624    312319623  af  Mac OS X HFS+

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: Unknown, but bootable
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 52576296:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 0b  FAT32 (CHS), active

Partition at LBA 95043624:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 4, type Mac OS X HFS+
 Listed in MBR as partition 4, type af  Mac OS X HFS+

Partition at LBA 91885609:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

---

### Post by liberalist on 2007-09-17
Thank you so much for your kind help. It now works :) I am so happy, because now I can run some Windows programs in a safe environment. Is there any way to download updates manually? I namely do not have an internet connection, but wish to stay up-to-date. Bluetooth does work, by the way.

---

### Post by pxwpxw on 2007-09-17
> **liberalist said:**
> Thank you so much for your kind help. It now works :) I am so happy, because now I can run some Windows programs in a safe environment. Is there any way to download updates manually? I namely do not have an internet connection, but wish to stay up-to-date. Bluetooth does work, by the way.

Glad it helped, have you now installed ubuntu704 successfully?

The Option key should get the Apple chooser, possibly  showing refit , macos , "windows".

If you do not have an internet connection how are you posting to the forum?

If you have the latest release - feisty (704) then updates should not be needed unltil the next release is finalised, when it will be available on a cd I expect, but you may find you need some additionl programs, which you might download using another system. 

Your comprehensive Partition report all looks good now - my refit version (refit .10 on a MacBook) does not show the full partition details, just the MBR and GPT tables. So I am curious - are you getting that from the refit partitioning tool?

---

