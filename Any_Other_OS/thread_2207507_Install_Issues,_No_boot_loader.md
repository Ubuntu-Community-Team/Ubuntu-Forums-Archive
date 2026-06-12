---
title: "Install Issues, No boot loader?"
date: 2014-02-23
forum: Any Other OS
---

### Post by pooopies on 2014-02-23
Hi, I was installing Linux mint 16 for a friend on his Vaio (SVP132190s) ultrabook with windows 8. Everything was going well, default install (2gb swap instead of 8, was the only change) for a dual boot off of a live USB. However, after the reboot I had a message "No operating system detected". So I rebooted off the live USB again and preformed a boot-repair, with default settings. I no longer get the "No operating system detected" message, but now it will not boot to anything unless the USB drive is in, and even then Grub only sees Mint on the usb drive (Seems that Grub is only installed on the USB, and doesn't see anything else). The bios settings are all default (Secure boot, EFI mode on) And I've tried to change those settings to no avail.

Here is the boot-repair log: [https://docs.google.com/document/d/16MIQijeL-oTUKZZRjX2QJsByEXdRB0Jzs6fRgYcIq88/edit?usp=sharing](https://docs.google.com/document/d/16MIQijeL-oTUKZZRjX2QJsByEXdRB0Jzs6fRgYcIq88/edit?usp=sharing)

Thank you for any assistance. I do not have the computer on me right now, though I will be troubleshooting on it again tomorrow night with any ideas that you all have. But I definitely will answer any questions to help with your assistance.

All the best.

---

### Post by fantab on 2014-02-23
```
[SIZE=1][COLOR=#222222][FONT=Arial]parted -l:

Model: ATA SAMSUNG MZHPU256 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
1      1049kB  274MB   273MB   fat32           EFI system partition          hidden
2      274MB   1819MB  1546MB  ntfs            Basic data partition          hidden, diag
3      1819MB  2092MB  273MB   fat32           EFI system partition          boot
4      2092MB  2226MB  134MB                   Microsoft reserved partition  msftres
5      2226MB  158GB   156GB   ntfs            Basic data partition          msftdata
10      158GB   176GB   17.7GB  ext4
11      176GB   184GB   8492MB  linux-swap(v1)
[/FONT][/COLOR][COLOR=#ff0000][FONT=Arial]8      184GB   184GB   1049kB                                                bios_grub[/FONT][/COLOR][/SIZE][COLOR=#222222][FONT=Arial][SIZE=1]
9      184GB   229GB   44.7GB  ext4
6      231GB   232GB   367MB   ntfs                                          hidden, diag
7      232GB   256GB   24.4GB  ntfs            Basic data partition          hidden, diag[/SIZE]
[/FONT][/COLOR]
```

The partition painted red is not needed if you have UEFI install. Its for booting Ubuntu from a GPT disk in BIOS mode. You don't need it. Either delete the partition or remove the 'bios_grub' flag with Gparted.
You seem to have installed GRUB to USB and Boot-Repair seems to have fixed it though.
Lets see. Change the boot order in UEFI/BIOs 'boot menu' to boot 'Ubuntu' first.
Also Boot-Repair appears to have renamed Windows EFI files and it needs to be undone. Run Boot-Repair again and check the option '**Restore EFI Backups**'... That should do.

Expect the thread to be moved to 'Other OS', as this is not really a Ubuntu issue.

Good Luck...

---

### Post by pooopies on 2014-02-24
Thank you very much! Will try this tomorrow and let you know.

Appreciate it.

---

### Post by Bucky Ball on 2014-02-24
*Thread moved to **Other OS/Distro Support**.*

Linux Mint is not officially supported in the main support areas here. You might also try posting [HERE]("http://forums.linuxmint.com/").

---

### Post by pooopies on 2014-02-25
Sorry about posting in the wrong forum.

Thank you for the assistance, and this fix got my windows boot going, but when I try to boot my linux off of a USB in UEFI mode I get the black screen, even when I do "NOMODESET" when booting grub. I tried the fixes from this thread: [http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063) to no avail. I also don't have the options in my boot configuration to boot off of a specific partition, only external or internal drive.  I have tried with secure mode on and off.

Thank you for any more assistance, progress is being made! I may not have access to this computer for a while after tomorrow, so I'll try anything I can.

Cheers

---

### Post by Bucky Ball on 2014-02-26
Are you sure you have secureboot, fastboot, and faststart (if you have Win8) switched off before attempting this? Faststart needs to be switched off by booting into Win8.

Change Win8 UEFI settings from OS:
[http://www.pcmag.com/article2/0,2817,2417361,00.asp](http://www.pcmag.com/article2/0,2817,2417361,00.asp)

---

### Post by oldfred on 2014-02-26
Some other Sony Vaio
 Sony Vaio Pro SVP-1x21 - Arch but similar settings needed for any Linux Haswell
[https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21](https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21)
Sony Vaio Pro 13 initrd issues - turn off UUID and libata.force=noncq splash parameter needed
[http://ubuntuforums.org/showthread.php?t=2189052](http://ubuntuforums.org/showthread.php?t=2189052)
Sony Vaio T13 
[http://ubuntuforums.org/showthread.php?t=2127699](http://ubuntuforums.org/showthread.php?t=2127699)

---

