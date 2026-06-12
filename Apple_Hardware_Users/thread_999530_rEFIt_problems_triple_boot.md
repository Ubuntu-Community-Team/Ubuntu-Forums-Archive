---
title: "rEFIt problems triple boot"
date: 2008-12-02
forum: Apple Hardware Users
---

### Post by sauce345 on 2008-12-02
I just got a new mac book pro and i am trying to get OS X, Vista 32 bit, and Ubuntu 8.10 installed.  I resized the hard drive with bootcamp and then installed vista and got it working.  Then i installed ubuntu and made sure to install the grub to /dev/sda4 in my case.  Any way all 3 icons appear on boot but the linux doesn't boot.  It just goes black and never comes out.  Here is my information from rEFIt partition tool:


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    453132327  Mac OS X HFS+
 3      453396480    537040887  Basic Data
 4      537040888    621439325  Basic Data
 5      621439326    625142414  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    453132327  af  Mac OS X HFS+
 3 *    453396480    537040887  07  NTFS/HPFS
 4      537040888    621439325  83  Linux

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

Partition at LBA 453396480:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 07  NTFS/HPFS, active

Partition at LBA 537040888:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 621439326:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

Does appear to be the correct setup? I can't see any problems with it and the linux still wont boot.  HELP!!:)

---

### Post by k956411 on 2008-12-02
i actually have a triple boot system which i set up ages ago. from what i recall boot camp doesn't allow you to do it this way.

check out this link 
[http://http://lifein0and1.com/2007/09/04/triple-boot-mac-os-x-ubuntu-and-windows-xp-on-macbook-pro-core-2-duo-part-1/]("http://http://lifein0and1.com/2007/09/04/triple-boot-mac-os-x-ubuntu-and-windows-xp-on-macbook-pro-core-2-duo-part-1/")

i still even have the printed instructions i used in the past in the office and if i remember when i get back i'll give you that link too.

---

### Post by cyberdork33 on 2008-12-02
Have you tried reinstalling grub?
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

---

### Post by k956411 on 2008-12-03
as promised here are some other links.

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu")

or

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp")

---

### Post by vakyoomluigi on 2008-12-03
I had a similar problem when I first tried triple-booting my macbook.  What I ended up doing (an overly complicated but successful solution) was restore the volume to one mac partition, resize the mac partition in disk utility, make 2 ubuntu partitions in the free space, erase one of the ubuntu partitions in the mac disk utility, then install windows on that.  If all else fails, give that a shot.

---

