---
title: "Triple Boot Problems - Third operating system nullifies the second"
date: 2008-03-07
forum: Apple Intel Users
---

### Post by alanlindsay on 2008-03-07
Hi, trying to triple boot OSX,XP and Ubuntu 7.10 on my MBP4.1. OSX is fine, then I split my disk into partitions for each OS. I have 15GB for Ubuntu, 65GB and 1GB for Linux swap. The installation of the second OS always goes fine and when completed  I can boot with rEFIt perfectly. When I install the third OS the installation goes fine but when i come to boot rEFit sees only OSX and the last OS I installed. Any ideas how I can fix this? I have OSX on (hd0,2), Linux on (hd0,3) XP on (hd0,4) and Linux swap is (hd0,5). Any help is much appreciated. Thanks,

AlanLindsay

---

### Post by alanlindsay on 2008-03-07
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    220348455  Mac OS X HFS+
 3      220348456    249645331  Basic Data
 4      249645332    388774238  MS Reserved
 5      388774663    390721934  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    220348455  af  Mac OS X HFS+
 3      220348456    249645331  83  Linux
 4 *    249645332    388774238  07  NTFS/HPFS

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 220348456:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 249645332:
 Boot Code: Windows NTLDR
 File System: NTFS
 Listed in GPT as partition 4, type MS Reserved
 Listed in MBR as partition 4, type 07  NTFS/HPFS, active

Partition at LBA 388774663:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

---

### Post by ferrous26 on 2008-03-07
I had a triple boot system running on my MBP 3.1 a while ago, and it was a bit of a pain to set up. I am not sure which of these steps you did properly or not, but here is how I did it:

Set up all three partitions from OS X, you cannot change the partition map properly using GParted or the Windows partition manager because the partition table is a hybrid. You can only have 4 primary partition because of MBR limitations, so I found it easier to use a swap file inside my Ubuntu partition instead of a swap partition.

Install Windows before Ubuntu and make Windows the last partition on the HDD otherwise the BIOS compatibility from Boot Camp will not work. Also, after you install Windows, boot to OS X and make sure you know where Windows put its boot loader. When I was trying the first few times, I made my Ubuntu and Windows partitions both FAT32 at first and Windows decided to put its boot loader in the Ubuntu partition and I didn't notice until everything failed.

When you install Ubuntu, make sure you install the boot loader to the same partition as where you are installing Ubuntu. 

Lastly, make sure you have rEFIt update the partition tables. I am not entirely sure about this, but it looks like the MBR part of the partition map is not picking up all the partitions.

---

### Post by alanlindsay on 2008-03-07
no obvious way to repair the MBR? Should I just start from scratch again?

---

### Post by cyberdork33 on 2008-03-07
> **ferrous26 said:**
> Set up all three partitions from OS X, you cannot change the partition map properly using GParted or the Windows partition manager because the partition table is a hybrid.gParted can update both partition types just fine. This was an issue only a very long time ago.
> **ferrous26 said:**
> You can only have 4 primary partition because of MBR limitations, so I found it easier to use a swap file inside my Ubuntu partition instead of a swap partition.yes but swap does not have to be a primary... besides Ubuntu reads the GPT and is not limited by the emulated BIOS, just windows.
> **ferrous26 said:**
> When you install Ubuntu, make sure you install the boot loader to the same partition as where you are installing Ubuntu.yep
> **ferrous26 said:**
> Lastly, make sure you have rEFIt update the partition tables. I am not entirely sure about this, but it looks like the MBR part of the partition map is not picking up all the partitions.I didn't notice anything myself, but it is good to check.

> **alanlindsay said:**
> no obvious way to repair the MBR? Should I just start from scratch again?you can repair the MBR with the Windows CD (Recovery Console: FIXMBR). And you can reinstall grub wherever you want:
[http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively)

---

### Post by alanlindsay on 2008-03-07
First of all, thanks for your responses guys. So the 3rd partition on my only disk is (hd0,2) right? because it starts counting from 0. This may be my problem. Trying to fix now

Alan

---

### Post by alanlindsay on 2008-03-07
Ok, got it working. Thanks very much.

Alan

---

### Post by cyberdork33 on 2008-03-08
> **alanlindsay said:**
> First of all, thanks for your responses guys. So the 3rd partition on my only disk is (hd0,2) right? because it starts counting from 0. This may be my problem. Trying to fix now

Alan
yes, please mark thread as solved

---

