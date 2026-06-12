---
title: "blank (black) screen when trying to load ubuntu 10.10 from refit"
date: 2011-04-01
forum: Apple Hardware Users
---

### Post by ransom630 on 2011-04-01
Today I got and formatted an external hard drive to use as a backup for os x/other stuff/maybe put ubuntu on it.

My system specifics are a Macbook model 1,1 / 1.83 ghz Intel Core Duo / 1gb ddr2 ram / 60 gb internal hd with one partition running OS X 10.5.8.

I have rEFIt 0.14 installed and working properly, i.e., it recognizes and boots OS X, cds, and sees my external drive.

I partitioned my new 500gb external usb drive, installed ubuntu (successfully), although every guide I read said there would be a place before install where I should choose to install grub to / rather than the MBR, but I saw no such option. Anyhow, it installed successfully. I rebooted and Tux appeared on the rEFIt menu. I synced the partitions, and that went fine. I then tried to boot ubuntu, and when I clicked the icon the gray screen with tux appeared, followed by a black screen. At this point nothing happens. I powered off and booted just fine from OS X and the live cd. 

Any solutions? Here is the output from Boot Info Script if that's helpful: It appears grub is installed to hdb2, which is the ext3 ubuntu install. Do I need to reinstall it to the MBR? Delete it from the MBR and install it to / (as instructed in the guides here, but for some reason I never saw this option on the editing partition aspect of the installation.)

Any help would be greatly appreciated.


============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb3 starts at sector 734527584.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2    *        409,640   116,948,055   116,538,416  af HFS


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   116,948,055   116,538,416 HFS+

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   524,550,206   524,550,144  af HFS
/dev/sdb2    *    524,550,222   734,527,565   209,977,344  83 Linux
/dev/sdb3         734,527,584   973,103,247   238,575,664   b W95 FAT32
/dev/sdb4         973,103,290   976,773,104     3,669,815   5 Extended
/dev/sdb5         973,103,292   976,773,104     3,669,813  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2860-11F4                              vfat       EFI                           
/dev/sda2        e4c72615-97ce-3232-9da7-70de4d9db81c   hfsplus    gunton                        
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        13fa721d-0951-3d78-b4ed-64c8e83798bc   hfsplus    os x backup                   
/dev/sdb2        e56ff849-2f11-45a8-8eff-d7f0d498979d   ext3                                     
/dev/sdb3        E9E2-1711                              vfat       WINDOWS                       
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        f7590278-43c1-43ab-92b5-ff33d4ae0fe5   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb2        /media/e56ff849-2f11-45a8-8eff-d7f0d498979d ext3       (rw,nosuid,nodev,uhelper=udisks)

---

