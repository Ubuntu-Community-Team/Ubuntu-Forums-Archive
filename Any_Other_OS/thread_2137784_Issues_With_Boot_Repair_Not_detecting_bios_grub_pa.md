---
title: "Issues With Boot Repair: Not detecting bios_grub partition"
date: 2013-04-22
forum: Any Other OS
---

### Post by VivaLaPanda on 2013-04-22
So, I'm dual booting linux for the first time on my computer. I run Windows 8 native on an unpartitioned 500gb internal HD. I want to install Linux Mint 13 Cinnamon 64bit to a partition on my 3TB External HD. I have made a live USB thumbdrive and gone through install, then rebooted into linux via the thumbdrive in order to enable Grub per [these]("http://forums.linuxmint.com/viewtopic.php?f=42&t=121912") instructions. I ran Boot Repair but got an error code.  I made a new unformatted 6mb partition and flagged it as bios_grub as per the error code when I attempted to run boot repair, but boot repair kept giving me the same error. I did step 10 and running as per the instructions and ```
[COLOR=#2E8B57][FONT=Monaco]sudo parted /dev/sda print[/FONT][/COLOR]
``` prints out 
```
Disk /dev/sdc: 3001GBSector size (logical/physical): 4096B/4096B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 5      24.6kB  33.6GB  33.6GB
 1      33.6GB  1626GB  1592GB               Ba
 2      1626GB  1730GB  105GB                Ba
 3      1730GB  2656GB  925GB                Ba
 4      2656GB  3001GB  345GB                      boot
 6      3001GB  3001GB  6291kB                     bios_grub
```
Which doesn't help me in determining my /boot/efi partiton..

---

### Post by Perfect Storm on 2013-04-22
Moved to Other OS/Distro Support.

---

### Post by VivaLaPanda on 2013-04-24
bump...

---

### Post by oldfred on 2013-04-24
Post the link to the full BootInfo report if it runs.
Your partition table looks corrupted though and that may be why you cannot get boot repair to run.
From one of my gpt drives(not UEFI):

```
fred@fred-Precise:~$ sudo parted /dev/sdb print
[sudo] password for fred: 
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name      Flags
 1      17.4kB  8225kB  8208kB                            bios_grub
 2      8225kB  26.2GB  26.2GB  ext4            MAVERICK
 3      26.2GB  29.4GB  3142MB  linux-swap(v1)
 4      29.4GB  160GB   131GB   ext4

```

Download from repository gdisk and see what it says.
sudo apt-get install gdisk

 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
      
 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by VivaLaPanda on 2013-04-26
GPT prints ```
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT
```

---

### Post by VivaLaPanda on 2013-04-26
It seems to be working psot reboot, will see how it goes.
[EDIT]
I was running boot repair then got fairly far then... ```
 GRUB failed to install to the following devices:                         &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; /dev/sdc                                                                 &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; Do you want to continue anyway? If you do, your computer may not start   &#9474;  
  &#9474; up properly.                                                             &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; Writing GRUB to boot device failed - continue? 
```
Here is the error report: [http://paste2.org/Yfat5tcn](http://paste2.org/Yfat5tcn)

---

### Post by oldfred on 2013-04-26
Did gdisk not show the 4 partitions?

Fdisk never shows gpt partitions so in Boot-repair that would be normal, but the first partition does not look correct. NTFS has to have in its PBR  or partition boot sector the same partition start & size info as the partition table. Yours does not match. It should be fixed with chkdsk from a Windows repair console or flash drive.

But it does not look like sdc1 starts at sector 2048 like it should.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

If grub does not see partition table correctly it will not install. Also grub now does not seem to install without the bios_grub partition if BIOS booting from a gpt partitioned drive.

      
 In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on

---

