---
title: "Ubuntu 18.04 on Macbook boot issues, blinking startup log screen. Tried a couple thin"
date: 2020-07-24
forum: Apple Hardware Users
---

### Post by genxcypher on 2020-07-24
Disclosure: I have asked this on AskUbuntu 3 days ago at time of post, but no one there has responded, so i'm trying here. 

Newb here, I've been trying to run Ubuntu 18.04 on my ol' 2009 Macbook (dual boot install alongside OS X 10.11 El Capitan, with swap partition) , I had it running pretty well for a couple days, then after installing some software and updates and stuff, I haven't been able to boot to it. Unfortunately I don't remember exactly what i did that may have triggered the issue, guess I'll have to start keeping logs of things for the 1st legs of my Linux journey. 

Anyway, what i get when I try to boot is, it starts out by looking pretty normal, I get the Ubuntu logo, then past that, i get a a screen that blinks between a plain black screen and what I guess is the startup log (picture attached, last line is "[ OK ] Started GNOME Display Manager."). [![boot_log_blinking][1]][1]

What I've tried so far is running boot-repair as found [here.]([https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)  "https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/") That didn't solve the issue for me unfortunately, but it did give me a lengthy log (am I using the correct term for that?) that I don't understand, which I'll also add at the bottom of this post. Would love any tips for reading these things, though I bet the moderators would prefer I ask that in a separate thread, so I won't "ask" here. 

I tried accessing the GRUB menu by holding Shift while trying to boot, but that too got me to a blinking screen. After that, I've also poked around with re-installing from a live USB stick, as advised also in the above link, but I was not shown an option to re-install, not even grayed-out. I found another post somewhere which advised I could try "Something Else" as an install option and it would still reinstall without deleting my data, but i found that not to be the case for me, it gave me a warning that my data would be deleted if I proceeded. 

Are there any other suggested diagnostic or troubleshooting steps I might try? I would greatly appreciate any thoughts or suggestions anyone may have. 

My machine specs:

Graphics: NVIDIA GeForce 9400M GPU

Broadcom Bluetooth Chipset

RAM: 6 GB DDR2 800 MHz SDRAM

CPU: Intel Core 2 Duo (2.13 GHz), 2 cores, L2: 3MB

Hard drive: Samsung 1 TB (~493 GB for Ubuntu, ~6 GB swap, rest Mac OS). Old school HD, not solid state.





What follows is the output when i ran boot-repair: 
```
> 

boot-repair-4ppa125                                              [20200714_2144]

============================= Boot Repair Summary ==============================


Unmount sdb2 from /media/ubuntu/LaCie Rugged 2TB/ to avoid special characters (& or \ or space) incompatibilities


Error: The primary GPT table is corrupt, but the backup appears OK, so that will be used.
grub-probe: error: cannot find a GRUB drive for /dev/sdc1.  Check your device.map.
grub-probe: error: cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of
sda4,
using the following options:        sda1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s  use-standard-efi-file


/boot/efi added in sda4/fstab
Mount sda1 on /mnt/boot-sav/sda4/boot/efi

Unhide GRUB boot menu in sda4/etc/default/grub

================= Reinstall the grub-efi-amd64-signed of sda4 ==================

grub-install --version
grub-install (GRUB) 2.02-2ubuntu8.15

efibootmgr -v from chroot before grub install
BootCurrent: 0000
BootOrder: 0000,0080
Boot0000* ubuntu    HD(1,GPT,0ffaf0c8-56e2-495c-9321-086de64e474f,0x28,0x64000)/File(EFIubuntushimx64.efi)
Boot0080*     PciRoot(0x0)/Pci(0xb,0x0)/Sata(0,0,0)/HD(2,GPT,a405b1f1-e0ab-4aef-9fef-ba63d392d423,0x64028,0x517d7a00)/File(SystemLibraryCoreServicesboot.efi)
Boot0082*     PciRoot(0x0)/Pci(0xb,0x0)/Sata(0,0,0)/HD(2,GPT,a405b1f1-e0ab-4aef-9fef-ba63d392d423,0x64028,0x3a2262b8)
BootFFFF*     PciRoot(0x0)/Pci(0x6,0x1)/USB(1,0)/HD(2,0,00000000000000000000000000000000,0x2eec,0x1340)/File(EFIBOOTBOOTX64.efi)

uname -r
5.3.0-28-generic

grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.
mkdir: cannot create directory â&#8364;&#732;/mnt/boot-sav/sdb1/EFIâ&#8364;&#8482;: Input/output error
cp /mnt/boot-sav/sda4/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sdb1/EFI/ubuntu/shimx64.efi
cp: cannot create regular file '/mnt/boot-sav/sdb1/EFI/ubuntu/shimx64.efi': No such file or directory
cp /mnt/boot-sav/sda4/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sdb1/EFI/ubuntu/
cp: cannot create regular file '/mnt/boot-sav/sdb1/EFI/ubuntu/': No such file or directory
df /dev/sda1
mv /mnt/boot-sav/sda4/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda4/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda4/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda4/boot/efi/EFI/Boot/bootx64.efi
cp /mnt/boot-sav/sda4/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda4/boot/efi/EFI/Boot/
mkdir: cannot create directory â&#8364;&#732;/mnt/boot-sav/sdb1/EFIâ&#8364;&#8482;: Input/output error
df /dev/sdb1
df: /dev/sdb1: No such file or directory
touch /mnt/boot-sav/sdb1/EFI/Boot/bootx64.efi.grb
touch: cannot touch '/mnt/boot-sav/sdb1/EFI/Boot/bootx64.efi.grb': No such file or directory
Error no /mnt/boot-sav/sdb1/EFI/Boot/bootx64.efi.grb

grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.

efibootmgr -v from chroot after grub install
BootCurrent: 0000
BootOrder: 0000,0080
Boot0000* ubuntu    HD(1,GPT,0ffaf0c8-56e2-495c-9321-086de64e474f,0x28,0x64000)/File(EFIubuntushimx64.efi)
Boot0080*     PciRoot(0x0)/Pci(0xb,0x0)/Sata(0,0,0)/HD(2,GPT,a405b1f1-e0ab-4aef-9fef-ba63d392d423,0x64028,0x517d7a00)/File(SystemLibraryCoreServicesboot.efi)
Boot0082*     PciRoot(0x0)/Pci(0xb,0x0)/Sata(0,0,0)/HD(2,GPT,a405b1f1-e0ab-4aef-9fef-ba63d392d423,0x64028,0x3a2262b8)
BootFFFF*     PciRoot(0x0)/Pci(0x6,0x1)/USB(1,0)/HD(2,0,00000000000000000000000000000000,0x2eec,0x1340)/File(EFIBOOTBOOTX64.efi)
Warning: NVram was not modified.

chroot /mnt/boot-sav/sda4 update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.3.0-1030-gke
Found initrd image: /boot/initrd.img-5.3.0-1030-gke
Found linux image: /boot/vmlinuz-5.3.0-62-generic
Found initrd image: /boot/initrd.img-5.3.0-62-generic
Found linux image: /boot/vmlinuz-5.3.0-28-generic
Found initrd image: /boot/initrd.img-5.3.0-28-generic
grub-probe: error: cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

Unhide GRUB boot menu in sda4/boot/grub/grub.cfg

An error occurred during the repair.

You can now reboot your computer.

Please do not forget to make your UEFI firmware boot on the Ubuntu 18.04.4 LTS entry (sda1/EFI/ubuntu/shimx64.efi file) !
You may also want to install Refind. ([https://help.ubuntu.com/community/ubuntupreciseon2011imac](https://help.ubuntu.com/community/ubuntupreciseon2011imac))

============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/grubx64.efi 
                       /efi/ubuntu/fwupx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdc: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg


================================ 1 OS detected =================================

OS#1:   Ubuntu 18.04.4 LTS on sda4

============================ Architecture/Host Info ============================

CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Ubuntu 18.04.4 LTS, bionic, x86_64)


===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.

efibootmgr -v
BootCurrent: 0000
BootOrder: 0000,0080
Boot0000* ubuntu    HD(1,GPT,0ffaf0c8-56e2-495c-9321-086de64e474f,0x28,0x64000)/File(\EFI\ubuntu\shimx64.efi)
Boot0080*     PciRoot(0x0)/Pci(0xb,0x0)/Sata(0,0,0)/HD(2,GPT,a405b1f1-e0ab-4aef-9fef-ba63d392d423,0x64028,0x517d7a00)/File(\System\Library\CoreServices\boot.efi)
Boot0082*     PciRoot(0x0)/Pci(0xb,0x0)/Sata(0,0,0)/HD(2,GPT,a405b1f1-e0ab-4aef-9fef-ba63d392d423,0x64028,0x3a2262b8)
BootFFFF*     PciRoot(0x0)/Pci(0x6,0x1)/USB(1,0)/HD(2,0,00000000000000000000000000000000,0x2eec,0x1340)/File(\EFI\BOOT\BOOTX64.efi)

bed45d1c9554cea09924d3814cb7c446   sda1/BOOT/fbx64.efi
256fe27540b54b71cf38110338247688   sda1/ubuntu/fwupx64.efi
64a633007e3d5a9a5943e417442548d6   sda1/ubuntu/grubx64.efi
4487628005555bfd4a4c0a47211e0700   sda1/ubuntu/mmx64.efi
f7a57b08bc7c1c85417ae4cea582d1d4   sda1/ubuntu/shimx64.efi
f7a57b08bc7c1c85417ae4cea582d1d4   sda1/BOOT/BOOTX64.efi
5783b82bc1dd7d612ca0447b737b35df   sda1/APPLE/EXTENSIONS/Firmware.scap


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    40 sectors * 512 bytes
sdb    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    40 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda4    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sdb1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdb2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

sda2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda4    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda2    : maybesepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    with--usr,    part-has-no-fstab,    std-grub.d,    sda
sda4    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sdb1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sdb
sdb2    : maybesepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    with--usr,    part-has-no-fstab,    std-grub.d,    sdb
sda1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 92DB2168-39F9-4D0D-9EBC-DA4EE7A6EDEE
          Start        End   Sectors   Size Type
sda1         40     409639    409600   200M EFI System
sda2     409640  975741663 975332024 465.1G Apple HFS/HFS+
sda3  976003808  987470183  11466376   5.5G Microsoft basic data
sda4  987732328 1952396390 964664063   460G Microsoft basic data
Disk sdc: 57.7 GiB, 61945675776 bytes, 120987648 sectors
Disk identifier: 0x6e037a9d
      Boot Start     End Sectors  Size Id Type
sdc1  *        0 4153407 4153408    2G  0 Empty
sdc2       12012   16939    4928  2.4M ef EFI (FAT-12/16/32)

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:4096:gpt:ATA HGST HTS541010A9:;
1:20.5kB:210MB:210MB:fat32:EFI System Partition:boot, esp;
2:210MB:500GB:499GB:hfs+:Macintosh HD:;
3:500GB:506GB:5871MB:linux-swap(v1):DOS_FAT_32_Untitled_3:msftdata;
4:506GB:1000GB:494GB:ext4:DOS_FAT_32_Untitled_2:msftdata;
sdb:2000GB:scsi:512:4096:gpt:LaCie Rugged Mini USB3:;
1:20.5kB:210MB:210MB:fat32:EFI System Partition:boot, esp;
2:210MB:2000GB:2000GB:hfs+:LaCie Rugged 2TB:;
sdc:61.9GB:scsi:512:512:gpt:PNY USB 3.0 FD:pmbr_boot;
1:20.5kB:210MB:210MB::EFI System Partition:boot, esp;
2:211MB:61.9GB:61.7GB::UBUNTU:msftdata;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                
â&#8221;&#339;â&#8221;&#8364;sda1 vfat     67E3-17ED                            0ffaf0c8-56e2-495c-9321-086de64e474f EFI                      EFI System Partition
â&#8221;&#339;â&#8221;&#8364;sda2 hfsplus  68aa2425-4600-3596-94cd-dfc1966e4e9f a405b1f1-e0ab-4aef-9fef-ba63d392d423 Macintosh HD             Macintosh HD
â&#8221;&#339;â&#8221;&#8364;sda3 swap     e6cf5fa2-44c4-4459-a4ae-5adc184b8a66 f0bd9fb9-057d-4658-bd43-e091f96bd65e                          DOS_FAT_32_Untitled_3
â&#8221;&#8221;â&#8221;&#8364;sda4 ext4     64b84d28-f28d-43f8-b7dd-3635192d8e3c 7d403be8-f666-4710-a721-fe2e9ecb2bd7                          DOS_FAT_32_Untitled_2
sdc    iso9660  2020-02-03-18-40-13-00                                                    Ubuntu 18.04.4 LTS amd64 
â&#8221;&#339;â&#8221;&#8364;sdc1 iso9660  2020-02-03-18-40-13-00               6e037a9d-01                          Ubuntu 18.04.4 LTS amd64 
â&#8221;&#8221;â&#8221;&#8364;sdc2 vfat     D055-8513                            6e037a9d-02                          Ubuntu 18.04.4 LTS amd64 

df (filtered): _________________________________________________________________

       Avail Use% Mounted on
sda1   173.5M  12% /mnt/boot-sav/sda1
sda2   313.6G  33% /mnt/boot-sav/sda2
sda4   376.5G  12% /mnt/boot-sav/sda4
sdb1               /mnt/boot-sav/sdb1
sdb2     1.7T   8% /mnt/boot-sav/sdb2
sdc         0 100% /cdrom

Mount options: __________________________________________________________________

sda1   rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sda2   ro,relatime,umask=22,uid=0,gid=0,nls=utf8
sda4   rw,relatime
sdb1   rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sdb2   ro,relatime,umask=22,uid=0,gid=0,nls=utf8
sdc    ro,noatime,nojoliet,check=s,map=n,blocksize=2048

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 64b84d28-f28d-43f8-b7dd-3635192d8e3c root hd0,gpt4 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda4/boot/grub/grub.cfg (filtered) ======================

Ubuntu   64b84d28-f28d-43f8-b7dd-3635192d8e3c
Ubuntu, with Linux 5.3.0-1030-gke   64b84d28-f28d-43f8-b7dd-3635192d8e3c
Ubuntu, with Linux 5.3.0-62-generic   64b84d28-f28d-43f8-b7dd-3635192d8e3c
Ubuntu, with Linux 5.3.0-28-generic   64b84d28-f28d-43f8-b7dd-3635192d8e3c
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda4/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=64b84d28-f28d-43f8-b7dd-3635192d8e3c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
# swap was on /dev/sda3 during installation
UUID=e6cf5fa2-44c4-4459-a4ae-5adc184b8a66 none            swap    sw              0       0
UUID=67E3-17ED  /boot/efi       vfat    defaults      0       1

======================= sda4/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda4: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 470.987483978 = 505.718960128  boot/grub/grub.cfg                             1
 520.949161530 = 559.364902912  boot/vmlinuz-5.3.0-1030-gke                    1
 472.924972534 = 507.799322624  boot/vmlinuz-5.3.0-28-generic                  2
 879.785068512 = 944.662024192  boot/vmlinuz-5.3.0-62-generic                  1
 520.949161530 = 559.364902912  vmlinuz                                        1
 472.924972534 = 507.799322624  vmlinuz.old                                    2
 521.261249542 = 559.700004864  boot/initrd.img-5.3.0-1030-gke                 2
 473.850284576 = 508.792868864  boot/initrd.img-5.3.0-28-generic               1
 881.875534058 = 946.906644480  boot/initrd.img-5.3.0-62-generic               4
 521.261249542 = 559.700004864  initrd.img                                     2
 473.850284576 = 508.792868864  initrd.img.old                                 1

===================== sda4: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 12693 Nov 11  2019 10_linux
-rwxr-xr-x 1 root root 11298 Nov 11  2019 20_linux_xen
-rwxr-xr-x 1 root root 12059 Nov 11  2019 30_os-prober
-rwxr-xr-x 1 root root  1418 Nov 11  2019 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Nov 11  2019 40_custom
-rwxr-xr-x 1 root root   216 Nov 11  2019 41_custom

====================== sdc/boot/grub/grub.cfg (filtered) =======================

Try Ubuntu without installing
Install Ubuntu
OEM install (for manufacturers)
Check disc for defects

==================== sdc: Location of files loaded by Grub =====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1


======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on sda1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 40 06 00 4f 0c 00 00  00 00 00 00 02 00 00 00  |.@..O...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 ed 17 e3 67 45  46 49 20 20 20 20 20 20  |..)...gEFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdc

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f3 06 b4 42 eb 15 eb 02  |...t.f.....B....|
00000070  31 c9 5a 51 b4 08 cd 13  5b 0f b6 c6 40 50 83 e1  |1.ZQ....[...@P..|
00000080  3f 51 f7 e1 53 52 50 bb  00 7c b9 04 00 66 a1 b0  |?Q..SRP..|...f..|
00000090  07 e8 44 00 0f 82 80 00  66 40 80 c7 02 e2 f2 66  |..D.....f@.....f|
000000a0  81 3e 40 7c fb c0 78 70  75 09 fa bc ec 7b ea 44  |.>@|..xpu....{.D|
000000b0  7c 00 00 e8 83 00 69 73  6f 6c 69 6e 75 78 2e 62  ||.....isolinux.b|
000000c0  69 6e 20 6d 69 73 73 69  6e 67 20 6f 72 20 63 6f  |in missing or co|
000000d0  72 72 75 70 74 2e 0d 0a  66 60 66 31 d2 66 03 06  |rrupt...f`f1.f..|
000000e0  f8 7b 66 13 16 fc 7b 66  52 66 50 06 53 6a 01 6a  |.{f...{fRfP.Sj.j|
000000f0  10 89 e6 66 f7 36 e8 7b  c0 e4 06 88 e1 88 c5 92  |...f.6.{........|
00000100  f6 36 ee 7b 88 c6 08 e1  41 b8 01 02 8a 16 f2 7b  |.6.{....A......{|
00000110  cd 13 8d 64 10 66 61 c3  e8 1e 00 4f 70 65 72 61  |...d.fa....Opera|
00000120  74 69 6e 67 20 73 79 73  74 65 6d 20 6c 6f 61 64  |ting system load|
00000130  20 65 72 72 6f 72 2e 0d  0a 5e ac b4 0e 8a 3e 62  | error...^....>b|
00000140  04 b3 07 cd 10 3c 0a 75  f1 cd 18 f4 eb fd 00 00  |.....<.u........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  dc 03 00 00 00 00 00 00  9d 7a 03 6e 00 00 80 00  |.........z.n....|
000001c0  01 00 00 7e e0 fd 00 00  00 00 40 60 3f 00 00 fe  |...~......@`?...|
000001d0  ff ff ef fe ff ff ec 2e  00 00 40 13 00 00 00 00  |..........@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages ================================

File descriptor 63 (pipe:[124846]) leaked on lvs invocation. Parent PID 4482: /bin/bash
```

---

