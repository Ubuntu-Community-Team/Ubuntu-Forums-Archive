---
title: "triple boot - windows doesn't boot"
date: 2008-03-09
forum: Apple Intel Users
---

### Post by FerdinandoPucci on 2008-03-09
Hi all,
I installed on my new macbook macosx Leopard, winXP and kubuntu following [http://wiki.onmac.net/index.php/Talk:Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Talk:Triple_Boot_via_BootCamp_Ubuntu).
Now this is the fdisk -l output:
Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26        7189    57540608   af  Sconosciuto
/dev/sda3            8642        9730     8739888    c  W95 FAT32 (LBA)
/dev/sda4   *        7190        8642    11665039+  83  Linux
Macosx and linux do boot, but winxp doesn't.

first of all, the partition table has a different partition order than the disk, as you can see from above. Does this matter?

I use refit to boot, when choosing windows I get the hal.dll error. I tryed several things to fix this, like what reported here
[http://support.microsoft.com/kb/314477/it](http://support.microsoft.com/kb/314477/it)
without results.

parted seg faults when used...

any hint?

thanks
Ferdinando

---

### Post by cyberdork33 on 2008-03-09
> **FerdinandoPucci said:**
> 
Now this is the fdisk -l output:
Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26        7189    57540608   af  Sconosciuto
/dev/sda3            8642        9730     8739888    c  W95 FAT32 (LBA)
/dev/sda4   *        7190        8642    11665039+  83  Linux
Macosx and linux do boot, but winxp doesn't.

first of all, the partition table has a different partition order than the disk, as you can see from above. Does this matter?yes it matters, it doesn't matter about the disk order it matters about the order in the partition table.

Also note that fdisk will only dump the contents of the MBR table, not the "real" partition table (GPT).

---

