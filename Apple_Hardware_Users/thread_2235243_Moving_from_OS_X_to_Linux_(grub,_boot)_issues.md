---
title: "Moving from OS X to Linux (grub, boot) issues"
date: 2014-07-19
forum: Apple Hardware Users
---

### Post by DigiAngel on 2014-07-19
So...my system is functional, but kind of a mess.  Exibit A:
```

Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot
 2      210MB   98.1GB  97.9GB  hfs+         Mavericks
 3      98.3GB  196GB   97.9GB  hfs+         Mav-Test
 4      196GB   894GB   698GB   ext3            <- data drive, no OS installed


Model: ATA ST240HM000-1G515 (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name                  Flags
 1      20.5kB  210MB  210MB  fat32        EFI System Partition  boot
 2      210MB   120GB  120GB  ext3         Apple_HFS_Untitled_2   <- this is actually Ubuntu install
 3      120GB   240GB  120GB  ntfs         Basic data partition  msftdata  <- Windows 7 64 bit

```
Problem #1, heh..it's an iMac, so it's a pain in the butt.  Issue #2, there is a user installed SSD, which is sdb shown above (full here [http://paste.ubuntu.com/7821863/]("http://paste.ubuntu.com/7821863/")).  I'm currently booting the box in the following manor:

Boot the box, goes to rEFInd, which is installed on I'm assuming sda1, which gets me a menu that defaults to the Linux bootloader (Grub) on I'm guessing sdb1.  At that point it's just going to Ubuntu.  When I want to boot into Windows, I have to hold the opt key on the Mac, then select Windows.  I don't use OS X anymore (because Mavericks), so in the end I'll only use Ubuntu and Windows 7 (games only) on sdb.  My first step I'm attempting is to get the Grub bootloader to be able to boot the Windows 7 install.  My next step is to get the box to boot first to Grub on sdb.  Then I'll remove the OS X partitions.  I'm currently stuck on phase one....getting Grub to boot /dev/sdb3.  Since this is gpt, here's the stanza I have:
```

menuentry "Windows 7 (bootmgr on /dev/sdb1)" --class windows --class os {
    insmod part_gpt
    insmod chain
    #insmod ntldr
    set root='(hd1,gpt1)'
    #ntldr ($root)/bootmgr 
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi

```
This gives me an error of:

error:  invalid EFI file path.

Thanks for any assistance you can provide.

---

### Post by yancek on 2014-07-19
I would add an:  insmod ntfs entry and change the chainloader entry to:  chainloader +1, leave the EFI path out.  The error specifically says it is wrong.

---

### Post by DigiAngel on 2014-07-20
Thanks for the response....changing the chanloader entry to +1 gets me:

error:  disk "hd1,gpt1" not found

---

### Post by coffeecat on 2014-07-20
*Thread moved to **Apple Users**.* This is the section for problems running Ubuntu on Apple hardware. Good luck!

I've added code tags to your terminal output in post #1 to restore the formatting you lost by posting it without code tags into your post.

---

### Post by DigiAngel on 2014-07-20
Ah..thanks coffeecat....every little bit of accuracy helps :)

---

### Post by oldfred on 2014-07-20
I do not have a Mac, but have not seen anyone boot Windows in UEFI mode from a Mac. They all are configured to be BIOS boot from a hybrid MBR/gpt configured drive.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

       Boot Windows from Mac with UEFI. Long thread 2009 thru 2014 
[http://forums.macrumors.com/showthread.php?t=696523](http://forums.macrumors.com/showthread.php?t=696523)

 Triple Boot MacbookPro (Lion, Win7, Ubuntu) Ubuntu in BIOS mode
[http://ubuntuforums.org/showthread.php?t=1908210](http://ubuntuforums.org/showthread.php?t=1908210)


 [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)

---

