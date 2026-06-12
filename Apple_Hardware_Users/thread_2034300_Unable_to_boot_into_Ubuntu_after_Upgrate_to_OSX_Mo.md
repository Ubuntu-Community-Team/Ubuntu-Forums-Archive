---
title: "Unable to boot into Ubuntu after Upgrate to OSX Mountain Lion"
date: 2012-07-28
forum: Apple Hardware Users
---

### Post by ibokg4 on 2012-07-28
Hi

I have managed to install OSX Mountain Lion on my macMini Mid 2010. This was not easy see [https://discussions.apple.com/message/19063113?ac_cid=tw123456#19063113](https://discussions.apple.com/message/19063113?ac_cid=tw123456#19063113) for further infos.

I am not able to boot into ubuntu anymore. :(

When i press the ALT key on boot i only see 2 Volumes "macintosh HD" and "Recovery HD". The 3rd named "Windows" (with ubuntu grub2 boot) is not available anymore (before installing ML it was there).

This are the infos refit prints with partition inspector:
```


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    557594087  Mac OS X HFS+
 3      557594088    558863623  Mac OS X Boot
 4      558863624    558865577  GRUB2 BIOS Boot
 5      558865578    608908546  Basic Data
 6      608908547    625142398  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    625142447  ee  EFI Protective

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

Partition at LBA 557594088:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot

Partition at LBA 558863624:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type GRUB2 BIOS Boot

Partition at LBA 558865578:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 5, type Basic Data

Partition at LBA 608908547:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 6, type Linux Swap

```

gdisk prints the following
```

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       557594087   265.7 GiB   AF00  Customer
   3       557594088       558863623   619.9 MiB   AB00  Recovery HD
   4       558863624       558865577   977.0 KiB   EF02  
   5       558865578       608908546   23.9 GiB    0700  
   6       608908547       625142398   7.7 GiB     8200  

```

How can i fix my system ?


Thanks in advance
Stefan

---

### Post by Niarbeht on 2012-07-28
My guess is that the grub MBR got nuked by the ML update.  But that's just a guess.

Usually, I fix that general kind of problem by booting off a rescue CD or USB stick, then chrooting to my Linux install and re-running grub-install.  There's some other magic you have to do, but I can't recall it off-hand.

Also, there's probably a better way.

Also also, have you considered trying to use grub-efi?

---

### Post by jackdaniels123123 on 2012-08-22
Im having the same exact problem with my macbook pro. After upgrading to Mountain Lion I can not boot into  my ubuntu partition anymore. I havent been able to find a working fix to reinstall grub2 efi

---

### Post by snip3r8 on 2012-08-22
In my experience with all of the operating systems Ive used , the boot loader is replaced by the one that comes with the most recently installed os.Have you tried booting with a live cd to see if you can find the partition?

---

