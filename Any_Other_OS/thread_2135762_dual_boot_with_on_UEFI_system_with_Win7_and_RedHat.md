---
title: "dual boot with on UEFI system with Win7 and RedHat"
date: 2013-04-15
forum: Any Other OS
---

### Post by asmirnov on 2013-04-15
Hello,
I have installed Oracle Linux 6.4 on a Lenovo T430s laptop with Windows7 UFEI with GPT partition table. 
Linux boot fine but Windows7 doesn't with message
Invalid EFI file path
Error 1: Filename must be either an absolute pathname or blocklist

My partitions during the Linux install were:
device      size    type           mount point
sda1        96M   EFI System  /boot/efi
sda2       128M  Uknown
sda3  240636M  ntfs
sda4       500M  /boot
sda5  235574M  volume

Boot loader installed into /dev/sda1

Before Linux was installed the result of running boot-repair-disk.iso is here

[http://paste2.org/1PAaDVap](http://paste2.org/1PAaDVap)

After Linux was installed if I do boot from the same CD and try Boot Repair it says LVM detected. Please use Ubuntu-Secure_remix, I have not done it.

This is what I have on the disk:

Under /boot/efi - BOOT EFI
Under /boot/efi/EFI - Boot Microsoft redhat
In /boot/efi/EFI/redhat       I have files grub.conf grub.efi
In /boot/efi/EFI/Boot         I have files bootwinre.efi bootx64.efi lenovobt.efi recovery.nsh
In /boot/efi/EFI/Microsoft/Boot I have files BCD BCD.LOG1 bootmgfw.efi bootmgr.efi BOOTSTAT.DAT memtest.efi….

I did run the the bootinfoscript, results are below:

Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

VolGroup-lv_root': _____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

VolGroup-lv_home': _____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

VolGroup-lv_swap': _____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       198,655       196,608 EFI System partition
/dev/sda2         198,656       460,799       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         460,800   493,283,327   492,822,528 Data partition (Windows/Linux)
/dev/sda4     493,283,328   494,307,327     1,024,000 Data partition (Windows/Linux)
/dev/sda5     494,307,328   976,773,119   482,465,792 Logical Volume Manager (LVM) partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0C72-A409                              vfat       SYSTEM_DRV
/dev/sda3        CA027594027585EB                       ntfs       Windows7_OS
/dev/sda4        bc426ea3-88c6-410c-9855-f69d6176b262   ext4       
/dev/sda5        jUY5Ft-9KG3-Sv21-s3KT-V9nQ-CAPJ-oh1Tdn LVM2_member 

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sr0         /live/image              iso9660    (ro,noatime)


=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             initramfs-2.6.32-358.el6.x86_64.img            2
            ?? = ??             initramfs-2.6.39-400.17.1.el6uek.x86_64.img    2
            ?? = ??             vmlinuz-2.6.32-358.el6.x86_64                  1
            ?? = ??             vmlinuz-2.6.39-400.17.1.el6uek.x86_64          1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on VolGroup-lv_root'


Unknown BootLoader on VolGroup-lv_home'


Unknown BootLoader on VolGroup-lv_swap'



=============================== StdErr Messages: ===============================

  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/VolGroup-lv_root': No such file or directory
hexdump: /dev/mapper/VolGroup-lv_root': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/VolGroup-lv_home': No such file or directory
hexdump: /dev/mapper/VolGroup-lv_home': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/VolGroup-lv_swap': No such file or directory
hexdump: /dev/mapper/VolGroup-lv_swap': No such file or directory
mdadm: No arrays found in config file or automatically


Please help.
Thank you
Anatoliy

---

### Post by oldfred on 2013-04-15
I do not know LVM, but know you need to add this first to an Ubuntu liveCD to get bootinfoscript to see the LVM.
sudo apt-get install lvm2

You need a correct chain entry to the Windows efi file in grub not a BIOS type chain entry. Ubuntu's version of os-prober creates BIOS entries not efi entires. 
You can manually add entries shown in the bug report.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

If entry has UUID change to your efi's UUID.
#I do not know how to show this for your Redhad, but you need to be root and get a list of UUIDs.
       sudo blkid -c /dev/null -o list
    

 Chainload entry:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)
menuentry "Windows 7 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,gpt1)'
  search --fs-uuid --no-floppy --set=root 4f84-ee2e
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

   menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

   menuentry "Windows bootmgfw.efi " {
search --fs-uuid --no-floppy --set=root 18FE-69D8
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

---

### Post by asmirnov on 2013-04-15
Hi, Thank you for the quick reply.

I had to roll all back since I screwed the Win7 install trying to write into EFI system partition instead of the /boot one that linux was creating.

Let me please ask you a basic one - having my partition layout as

sda1        96M   EFI System  /boot/efi
sda2       128M  Uknown
sda3  240636M  ntfs
sda4       500M  /boot
sda5  235574M  volume

shall boot loader be installed into /dev/sda4?

Just want to confirm if this is 100% correct statement... Cause like I said I thought let me try /boot/efi and that screwed windows :(

Once I have Linux installed and booted I am planning to try and fix grub following along the lines that you mentioned.

And just to make sure I read your response right - I am using (I think, wanted confirm) GRUB, not GRUB2, correct?

Thank you
Anatoliy

---

### Post by oldfred on 2013-04-15
If you are configured to boot with BIOS, you install grub2's boot loader into the MBR. And with most LVM type installs you have a separate /boot partition outside the LVM that has grub menu, grub files, & the kernel to boot with.
But with UEFI, all systems install boot loaders into the efi partition. Each system has its own folder and since it is larger than MBR, may have more support files for the boot loader, but normally grub menu & kernel is still in /boot partition or folder in root if /boot not a separate partition.
I do not know about Redhat, but some have posted with the Fedora version that they do not use the LVM and just install to a standard partition. The advantage of LVM is flexibility of moving partitions around but you have greater complexity. But when you already have other partitions to dual boot you are not getting any of the LVM advantage.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

---

### Post by asmirnov on 2013-04-20
Problem solved.
You are correct - the syntax in the grub entry was not correct, the syntax that did work for me was
rootnoverify (hd0,0)
chainloader /EFI/Microsoft/Boot/bootmgfw.efi

Thank you for helping me out.

---

