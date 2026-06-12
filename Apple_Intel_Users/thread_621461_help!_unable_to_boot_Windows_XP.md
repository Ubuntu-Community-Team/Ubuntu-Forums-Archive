---
title: "help! unable to boot Windows XP"
date: 2007-11-23
forum: Apple Intel Users
---

### Post by 4LTR on 2007-11-23
Hi

I am trying to triple boot my Macbook, I installed Windows XP successfully via boot camp.
Then I made two partitions using Apple's disk utility, one for Ubuntu, and another for the swapfile.
I then installed Ubuntu on to the partition for Ubuntu and although I installed Ubuntu successfully,
I now can't boot from Windows XP, it only boots the Mac and the Ubuntu partition.
But the windows partition still appears on the Mac's desktop.

I tried running the Windows recovery console, to configure the bootcfg but windows couldn't detect a  disk. Then I installed rEFIt, and the same, it only boots the Mac and the Ubuntu partition.

I was wondering if there is any way I can get my Macbook to boot successfully from the Windows partition or am I going to have to backup my Mac, format the disk and restart the process again.

Can anyone help me?

---

### Post by 4LTR on 2007-11-23
Here is the rEFIt partition inspector report if that helps:


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    105267239  Mac OS X HFS+
 3      105529384    107626535  Linux Swap
 4      107626536    124403751  Basic Data
 5      124403752    156301447  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    105267239  af  Mac OS X HFS+
 3      105529384    107626535  82  Linux swap / Solaris
 4      107626536    124403751  83  Linux

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 105529384:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Linux Swap
 Listed in MBR as partition 3, type 82  Linux swap / Solaris

Partition at LBA 107626536:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 124403752:
 Boot Code: Windows NTLDR
 File System: NTFS
 Listed in GPT as partition 5, type Basic Data

---

### Post by cyberdork33 on 2007-11-24
What happens when you select the Windows Icon in rEFIt?

---

### Post by 4LTR on 2007-11-24
When I select the Windows Icon, it boots up Ubuntu.

---

### Post by cyberdork33 on 2007-11-24
> **4LTR said:**
> When I select the Windows Icon, it boots up Ubuntu.
It starts Grub? 

You overwrote your MBR bootloader when you installed Ubuntu. See the Multi Booting Properly Guide in my signature.

---

### Post by 4LTR on 2007-11-24
Here is what the grub command line came up with:

grub> find /boot/grub/stage1
 (hd0,3)

Is that partition the one where I set the ‘root’ and install grub to?

---

### Post by 4LTR on 2007-11-25
> **cyberdork33 said:**
> 
You overwrote your MBR bootloader when you installed Ubuntu. See the Multi Booting Properly Guide in my signature.

Followed your guide and Mac OS X and Grub/Ubuntu work fine, but Windows can't find an operating system is there something wrong with the Windows Partition?

---

### Post by 4LTR on 2007-11-25
> **4LTR said:**
> Followed your guide and Mac OS X and Grub/Ubuntu work fine, but Windows can't find an operating system is there something wrong with the Windows Partition?

The Windows partition works fine within Mac OS X by the way.

---

### Post by cyberdork33 on 2007-11-25
> **4LTR said:**
> Followed your guide and Mac OS X and Grub/Ubuntu work fine, but Windows can't find an operating system is there something wrong with the Windows Partition?
I don't understand what this means. you need to state precisely what you are doing and any error messages you are getting as a result.

---

### Post by aletheianalex on 2007-11-26
> **cyberdork33 said:**
> I don't understand what this means. you need to state precisely what you are doing and any error messages you are getting as a result.

Agreed.  You could try taking a peek at the MBR in the Windows recovery console so that you can see what Windows is seeing... but don't make any changes there just yet until you let us know what is going on.

---

