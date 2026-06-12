---
title: "Refit Ubuntu AND Windows both boot to GRUB...HELP?"
date: 2010-08-03
forum: Apple Hardware Users
---

### Post by ChooChooTron on 2010-08-03
First up, assume i know nothing about computers.
I have a MBP 5,5, and choosing the logo for windows brings up the grub menu, as does choosing ubuntu's logo. I've read a lot saying i need to install GRUB natively under ubuntu, but I've had no luck doing so. can anyone essentially walk me through this step by step?
or offer alternatives?

MBP 5,5 
OS X 10.6.4
Win 7
ubuntu 10.04

thanks guys.

---

### Post by ChooChooTron on 2010-08-04
sorry for the double post, but after further investigation, i am having a ot more trouble figuring out why this is an issue
according to rEFIt's partition inspector, the windows partition isnt even set up to go to grub

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    328955295  Mac OS X HFS+
 3      329218048    407341055  Basic Data
 4      407341056    485464063  Basic Data
 5      485464064    488396799  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    328955295  af  Mac OS X HFS+
 3 *    329218048    407341055  07  NTFS/HPFS
 4      407341056    485464063  83  Linux

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
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 329218048:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 07  NTFS/HPFS, active

Partition at LBA 407341056:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 485464064:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

```

please help if you can
thanks.

---

### Post by alphonce on 2010-08-07
first: i recommend that you create a boot partition for linux 128 mb with ext2 is enough, then it will be much easier to handle kernels and ather stuff.

if you do this, then you have to remove the linux partition och redo the two partitions, but if i guess right you've never booted the linux so you wont loose anything.

you then have to reinstall linux and when you do so, setup the boot partition to mount at /boot (you have to partition the hard drive manually). the step after when a lot of information is viewed in a window and you have to press begin/start/accept (something like that). there is also a configure/advance (?) button which you press and then choose to install grub into the boot partition.

second: if you choose to keep your setup, you have to start the install-cd and then chroot into your linux partition, there are guides ex here [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=6#doc_chap1]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=6#doc_chap1") and skip the first part with the mirrors. the just install grub to the partition```
grub-install /dev/sda4
```or whatever the name of the linux partition is.

good luck

---

### Post by ChooChooTron on 2010-08-10
hey thanks, that was pretty much the solve.
i ended up totally deleting grub from inside my ubuntu partition, then booting to the 10.04 live cd, mounting my /dev/sda4 and messing with it until i convinced grub to reinstall under that partition only
then i booted to the windows 7 cd ,  letting it find ONLY my windows partition on it's own, and at the command prompt typing
```
X:\BootRec.exe /FixMbr
```
(Don't forget the space before the /)
and it told Windows not to look for grub, and replaced the windows bootloader.
Now everything works great!
thanks!

---

