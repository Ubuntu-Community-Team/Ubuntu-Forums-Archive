---
title: "Dual Boot with Windows XP - grub problems"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by mihaic on 2005-12-18
Hi all,

   I don't know if any of you encountered such problems, but by searching the forum I ahven't been able to find a satisfying solution.
  My problem is that I have a Windows XP installed on an NTFS partition but after installing the Ubuntu 5.10 Breezy Badger, grub does not recognize the windows partition, thus rendering me unable to boot windows. 
  My grub menu.lst has this entry for windows (added by me because at install it didn't even ask me about other operating systems) 

[I]
title		Windows XP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/I]

Also I have 2 other FAT32 partitions on my disk with data for windows. Breezy seems to be able to mount these automatically while, it gives me an error when it tries to mount the NTFS system partition. The syslog has the following entry regarding this:
[I]
Dec 18 14:40:18 amras kernel: [   77.573211] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
Dec 18 14:40:18 amras kernel: [   77.573218] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[/I]

Any help or advice is very wellcome.
  Thanks,
  Mihai

---

### Post by bscbrit on 2005-12-18
This is unusual as Breezy has recognised ntfs drives on 5 separate computer installations here.  Did you use the MBR option for installing grub?

---

### Post by mihaic on 2005-12-18
[QUOTE=bscbrit]This is unusual as Breezy has recognised ntfs drives on 5 separate computer installations here.  Did you use the MBR option for installing grub?[/QUOTE]

Nope, I haven't done that. I'll look it up in the grub manual and try it to see what happens. I am kind of stressed about this because I don't want to go through installing windows again (I just did that yesterday) - too bad I haven't backed it up ](*,) 

Thanks for the reply,
Mihai

---

### Post by plcdfa on 2005-12-18
Well u don't need to reinstall windows anyway, you can rewrite its bootloader in MBR from the recovery console ("fixmbr" i think it is, but somebody please correct me if I'm wrong - I don't use XP. :)) Then it should boot straight into Windows next time. Then you can start worring about booting into linux. :) You can try to reinstall grub correctly from the ubuntu cd (don't need to reinstall ubuntu!) , or if you've really put it in the ext3 partition's boot sector instead of the MBR, than you can edit your boot.ini in windows so the ntloader displays a menu and calls grub.

---

### Post by mihaic on 2005-12-19
[QUOTE=plcdfa]Well u don't need to reinstall windows anyway, you can rewrite its bootloader in MBR from the recovery console ("fixmbr" i think it is, but somebody please correct me if I'm wrong - I don't use XP. :)) Then it should boot straight into Windows next time. Then you can start worring about booting into linux. :) You can try to reinstall grub correctly from the ubuntu cd (don't need to reinstall ubuntu!) , or if you've really put it in the ext3 partition's boot sector instead of the MBR, than you can edit your boot.ini in windows so the ntloader displays a menu and calls grub.[/QUOTE]

  First of all, thanks for the advice. I have tried to remove it by using XP's fixmbr from the XP boot cd recovery console, I even used fdisk /mbr on it after booting with a dos disk, but that didn't seem to work either, grub still displayed on bootup.
  It seems that when I installed grub, I did it in the boot sector of the NTFS XP partition so editing the boot.ini might have been a good choice, if I knew about it, but I already reformated the partition and reinstalled XP again (if it weren't for the games I would not go through this trouble :D). Now all that remains to be done is to reinstall Ubuntu since I deleted the Linux ext3 partitions also :).
  What I haven't mention in the begining is that first I had Hoary installed, then I reinstalled XP and tried to recover grub using Hoary install cd. This is where I scrued up by running "grub-install /dev/sda1" where /dev/sda1 is the windows primary partition. After this, I taught that by installing Linux from scratch it would detect windows again and everything would be ok, besides I just got my Breezy cd, so I said why not upgrade if I have the occasion :).
  The conclusion is that I would not recommend anyone to install windows after Linux. If you want a dual boot, do the other way around, and you'll spare yourself some headaches :). If you really, really, really have no choice, backup your system before doing this and read carefully the grub and grub-install documentation before runing grub-install on some partition.

Thanks,
Mihai

---

