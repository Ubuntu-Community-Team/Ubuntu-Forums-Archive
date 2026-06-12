---
title: "Upgrade Dual-Boot with Leopard to Snow Leopard"
date: 2009-12-18
forum: Apple Hardware Users
---

### Post by brennon80 on 2009-12-18
Currently dual-booting Karmic and Leopard using rEFIt.  I'd like to upgrade the Leopard installation to Snow Leopard.  Any problems I might have?

Thanks,
Brennon

---

### Post by linuxopjemac on 2009-12-18
You might have to reinstall rEFIt?

---

### Post by thinktyler on 2009-12-19
I had no problems upon my upgrade with the DVD5 version of the upgrade.

---

### Post by brennon80 on 2009-12-21
> **linuxopjemac said:**
> You might have to reinstall rEFIt?
Alright...what would be the process for doing this?  Just with a Live CD?

---

### Post by brennon80 on 2009-12-21
> **brennon80 said:**
> Alright...what would be the process for doing this?  Just with a Live CD?

Also, what information should I gather in advance in case I do need to reinstall rEFIt?

---

### Post by tom4everitt on 2009-12-22
I don't think you will need to reinstall refit. If you do, there's no information you will need to gather before; refit doesn't need a lot of configuration...

---

### Post by tom4everitt on 2009-12-22
> **brennon80 said:**
> Alright...what would be the process for doing this?  Just with a Live CD?

In OS X you just go to their website, download it, and install just like any program.

[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

---

### Post by brennon80 on 2010-01-06
Just thought I'd send an update.  Updated to Snow Leopard without a hitch!

---

### Post by squinter on 2010-11-28
I run dual-boot macos and ubuntu. I just upgraded to snow leopard. Refit menu still showing but when I select the linux icon, now it stuck on the penguin picture (it doesn't boot to ubuntu anymore). I checked the partition and the ubuntu partition is still there and the flag still says bootable.

When I ran the snow leopard upgrade, at first it didn't want to install. So I used GPartition Live CD and shrink the MacOS partition by 253MB and upgrade went well. MacOS runs fine.

I run Partition Inspector on Mac and got this information:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    154818404  Mac OS X HFS+
 3      155336744    306086744  EFI System (FAT)
 4      306086745    312581774  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    154818404  af  Mac OS X HFS+
 3 *    155336744    306086744  83  Linux
 4      306086745    312581774  82  Linux swap / Solaris

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

Partition at LBA 155336744:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 3, type EFI System (FAT)
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 306086745:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

Anyone can help fix this?

---

### Post by squinter on 2010-11-28
Never mind it is working now. I think it just needed a shutdown from the refit menu.

---

