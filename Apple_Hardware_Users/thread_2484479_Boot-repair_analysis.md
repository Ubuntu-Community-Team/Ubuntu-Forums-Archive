---
title: "Boot-repair analysis"
date: 2023-02-28
forum: Apple Hardware Users
---

### Post by pbutterworth on 2023-02-28
Hi,

I installed Ubuntu on a mac, supposed to be dual boot, but Grub has replaced the boot manager and i cant boot into MacOS. Any ides, will boot-repair solve this?

and its [https://paste.ubuntu.com/p/s7tXFpRkp9/](https://paste.ubuntu.com/p/s7tXFpRkp9/)

Tanks
Paul

---

### Post by pbutterworth on 2023-02-28
oops sorry, paste bere:
> ```

boot-repair-4ppa2056                                              [20230228_0913]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => libparted MBR boot code is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files:        /EFI/refind/refind.conf /efi/BOOT/fbx64.efi 
                       /efi/BOOT/mmx64.efi /efi/OC/OpenCore.efi 
                       /efi/refind/refind_x64.efi /efi/tools/gptsync_x64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg 
                       /efi/OC/Drivers/OpenCanopy.efi 
                       /efi/OC/Drivers/OpenLinuxBoot.efi 
                       /efi/OC/Drivers/OpenRuntime.efi 
                       /efi/OC/Drivers/ResetNvramEntry.efi 
                       /efi/OC/Tools/BootKicker.efi 
                       /efi/OC/Tools/OpenShell.efi

sda2: __________________________________________________________________________

    File system:       apfs
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda2: unknown filesystem type 'apfs'.

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 40.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       apfs
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sdc2: unknown filesystem type 'apfs'.


================================ 1 OS detected =================================

OS#1:   Ubuntu 22.04.2 LTS on sdb1

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: 2nd Generation Core Processor Family Integrated Graphics Controller from Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-5.19.0-32-generic root=UUID=7d910750-b848-4835-8c02-878783b8902c ro quiet splash
df -Th / : /dev/sdb1      ext4  916G  8.5G  861G   1% /

===================================== UEFI =====================================

BIOS/UEFI firmware: 135.0.0.0.0(0.1) from Apple Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled - This system doesn't support Secure Boot.
BootCurrent: 0000
Timeout: 5 seconds
BootOrder: 0000,0001,0080
Boot0000* ubuntu    HD(1,GPT,7993bf1a-4f1c-4ab4-90cc-644acfc46e4f,0x28,0x64000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* OpenCore    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,0,0)/HD(1,GPT,7993bf1a-4f1c-4ab4-90cc-644acfc46e4f,0x28,0x64000)/File(EFI\OC\OpenCore.efi)
Boot0080* Mac OS X    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,0,0)/HD(2,GPT,2eafb08c-ff78-4496-bd5a-dfc163ae1079,0x64028,0x7456ce40)
Boot0081* Mac OS X    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,0,0)/HD(2,GPT,5352de37-7ac9-44d9-be9d-44b95b73d85b,0x64028,0x7456ce40)
BootFFFF*     PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,0,0)/HD(2,GPT,000054e0-2e94-0000-e07f-0000354a0000,0x64028,0x3a1ec0c0)/File(\System\Library\CoreServices\boot.efi)

a9c517741ac31962d7feb152948ad1ee   sda1/BOOT/fbx64.efi
a660182adef313615746a665966d2ccc   sda1/BOOT/mmx64.efi
f9d47e038dc3e9a97781879eea495f63   sda1/OC/OpenCore.efi
f4fab70b6301572af35b245b66c69058   sda1/refind/refind_x64.efi
619487d362e24157692bcb4db9682341   sda1/tools/gptsync_x64.efi
5ddf997e8b025bfbc2009e85b32f60dc   sda1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   sda1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sda1/ubuntu/shimx64.efi
c29931cb7e18c10ca91ee111fc25684a   sda1/OC/Drivers/OpenCanopy.efi
1baaacdf5b8ecbc81fdbbe93540551ce   sda1/OC/Drivers/OpenLinuxBoot.efi
6a45a4f4e219e835b11b7ac20d97d799   sda1/OC/Drivers/OpenRuntime.efi
0f985d7157e40b1d0d5a850907fa7195   sda1/OC/Drivers/ResetNvramEntry.efi
755be7c4b103038621dbfd54a16ac0b2   sda1/OC/Tools/BootKicker.efi
3464e63148d6b804f14a14e7514912ab   sda1/OC/Tools/OpenShell.efi
64349b3622c65f495a99dbf6102496e3   sda1/BOOT/BOOTX64.efi
5783b82bc1dd7d612ca0447b737b35df   sda1/APPLE/EXTENSIONS/Firmware.scap
8ed8a30d7cc39f5b1c8ab1fa84840990   sda1/APPLE/FIRMWARE/MM51.scap

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sdb    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sdc    : is-GPT,    no-BIOSboot,    has---ESP,     usb-disk,    not-mmc, no-os,    no-wind,    40 sectors * 512 bytes
sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    no-wind,    40 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sdb1    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sdc2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdc1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

sdb1    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sdb1    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sdb
sdc2    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sda2    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: C0A620FC-9168-4C82-A02A-A51CE1388080
       Start        End    Sectors   Size Type
sda1      40     409639     409600   200M EFI System
sda2  409640 1952255591 1951845952 930.7G Apple APFS
Disk sdb: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0x660e104f
      Boot Start        End    Sectors   Size Id Type
sdb1  *     2048 1953523532 1953521485 931.5G 83 Linux
Disk sdc: 29.72 GiB, 31914983424 bytes, 62333952 sectors
Disk identifier: 9BF93208-1B02-4E11-960E-6684CB1E3C52
       Start      End  Sectors  Size Type
sdc1      40   409639   409600  200M EFI System
sdc2  409640 62333911 61924272 29.5G Apple APFS

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:4096:gpt:ATA ST1000LM014-1EJ1:;
1:20.5kB:210MB:210MB:fat32:EFI System Partition:boot, esp;
2:210MB:1000GB:999GB::Mac 1TB Hybrid:;
sdb:1000GB:scsi:512:4096:msdos:ATA WDC WD10JPVT-75A:;
1:1049kB:1000GB:1000GB:ext4::boot;
sdc:31.9GB:scsi:512:512:gpt:Generic STORAGE DEVICE:;
1:20.5kB:210MB:210MB:fat32:EFI System Partition:boot, esp;
2:210MB:31.9GB:31.7GB:::;

Free space >10MiB: ______________________________________________________________

sda: 953250MiB:953870MiB:620MiB

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL PARTLABEL
sda                                                                                             
&#9500;&#9472;sda1 vfat     67E3-17ED                            7993bf1a-4f1c-4ab4-90cc-644acfc46e4f EFI   EFI System Partition
&#9492;&#9472;sda2 apfs     97cbcaf2-3e9a-4e38-bccf-7352ef5cf8b3 2eafb08c-ff78-4496-bd5a-dfc163ae1079       Mac 1TB Hybrid
sdb                                                                                             
&#9492;&#9472;sdb1 ext4     7d910750-b848-4835-8c02-878783b8902c 660e104f-01                                
sdc                                                                                             
&#9500;&#9472;sdc1 vfat     67E3-17ED                            c0bcc597-5ca0-4e83-9553-cb55e1804633 EFI   EFI System Partition
&#9492;&#9472;sdc2 apfs     220fe6af-4991-40cd-8995-1b8ca3e78d9d 815a372f-fd27-4624-95c8-ac7d53755b1f       

Mount points (filtered): _______________________________________________________

                                Avail Use% Mounted on
/dev/sda1                      152.1M  23% /mnt/boot-sav/sda1
/dev/sdb1                      860.8G   1% /
/dev/sdc1                      196.9M   0% /mnt/boot-sav/sdc1

Mount options (filtered): ______________________________________________________


==================== sda1/EFI/refind/refind.conf (filtered) ====================

timeout 20
use_nvram false
menuentry Linux {
    icon EFI/refind/icons/os_linux.png
    volume 904404F8-B481-440C-A1E3-11A5A954E601
    loader bzImage-3.3.0-rc7
    initrd initrd-3.3.0.img
    options "ro root=UUID=5f96cafa-e0a7-4057-b18f-fa709db5b837"
    disabled
}
menuentry "Arch Linux" {
    icon     /EFI/refind/icons/os_arch.png
    volume   "Arch Linux"
    loader   /boot/vmlinuz-linux
    initrd   /boot/initramfs-linux.img
    options  "root=PARTUUID=5028fa50-0079-4c40-b240-abfaf28693ea rw add_efi_memmap"
    submenuentry "Boot using fallback initramfs" {
        initrd /boot/initramfs-linux-fallback.img
    }
    submenuentry "Boot to terminal" {
        add_options "systemd.unit=multi-user.target"
    }
    disabled
}
menuentry Ubuntu {
    loader /EFI/ubuntu/grubx64.efi
    icon /EFI/refind/icons/os_linux.png
    disabled
}
menuentry "ELILO" {
    loader \EFI\elilo\elilo.efi
    disabled
}
menuentry "Windows 7" {
    loader \EFI\Microsoft\Boot\bootmgfw.efi
    disabled
}
menuentry "Windows via shell script" {
    icon \EFI\refind\icons\os_win.png
    loader \EFI\tools\shell.efi
    options "fs0:\EFI\tools\launch_windows.nsh"
    disabled
}
menuentry "My macOS" {
    icon \EFI\refind\icons\os_mac.png
    volume "macOS boot"
    loader \System\Library\CoreServices\boot.efi
    disabled
}
menuentry "macOS via BootNext" {
    icon /EFI/refind/icons/os_mac.png
    firmware_bootnum 80
    disabled
}

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 7d910750-b848-4835-8c02-878783b8902c root hd1,msdos1 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Ubuntu   7d910750-b848-4835-8c02-878783b8902c
Ubuntu, with Linux 5.19.0-32-generic   7d910750-b848-4835-8c02-878783b8902c
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sdb1/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=7d910750-b848-4835-8c02-878783b8902c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=67E3-17ED  /boot/efi       vfat    umask=0077      0       1

======================= sdb1/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 228.685409546 = 245.549088768  boot/grub/grub.cfg                             1
   4.274410248 = 4.589613056    boot/vmlinuz                                   2
   4.274410248 = 4.589613056    boot/vmlinuz-5.19.0-32-generic                 2
   7.129589081 = 7.655337984    boot/initrd.img                                1
   7.129589081 = 7.655337984    boot/initrd.img-5.19.0-32-generic              1
   7.129589081 = 7.655337984    boot/initrd.img.old                            1

===================== sdb1: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec  2 15:18 10_linux
-rwxr-xr-x 1 root root 43031 Dec  2 15:18 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Dec  2 15:18 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec  2 15:18 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec  2 15:18 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Sep 20 04:18 35_fwupd
-rwxr-xr-x 1 root root   214 Dec  2 15:18 40_custom
-rwxr-xr-x 1 root root   215 Dec  2 15:18 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sdb1,
using the following options:  sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.2 LTS entry (sda1/efi/****/grub****.efi (**** will be updated in the final message) file) !
You may also want to install Refind. ([https://help.ubuntu.com/community/ubuntupreciseon2011imac](https://help.ubuntu.com/community/ubuntupreciseon2011imac))

```

---

### Post by ajgreeny on 2023-02-28
Moved to **Apple hardware users** which is more appropriate.

---

### Post by MAFoElffen on 2023-02-28
Please go back to your post #2, then Edit Post > Advanced > Select the text of the boot-info report (highlight) > Then select the '#' Icon to wrap that report with Code Tags. Please do the same for raw output or commands. One, it makes it easier to read. Two, raw output does weird things to the Forums Software.

Hmmm. I have Ubuntu dual booted with Snow Leopard & Lion, on an older Mac Pro. What I see when I boot up is the Grub2 Menu. That is the normal boot loader after an install. 

If you press the "Option Key" on startup (Hold down directly after pressing the power button)... Then you will get the thumbnails of disks, with your MacOS Name (MacOS), another saying EFI Boot (Grub), and another saying Recovery HD (The MacOS Recovery Menu). 

Does that answer your question?

Do you not have any entries after Ubuntu, then #Advanced options for Ubuntu, ... Then Mac OS X (64-bit) (on /dev/sdaX)?

---

### Post by pbutterworth on 2023-02-28
So maybe ts this keyboard, have had issues before, Its a windows wireess keyboard, I'll dig out an old hard wired one this evening an see if that works any better. Is there a way to get it to automatically show a boot selection every time, even if it times out to one O/S after a period of time, rather than default to one O/S?

---

### Post by pbutterworth on 2023-03-01
So, MAFoElffen thank you, you are indeed correct, when I connected a hard wired keyboard I could get back into the boot menu and get back into MacOS.

Is there a way to force the O/S selection menu on each boot without pressing Option? Ideally I would liek the menu to come up for a period of time, thenm if no interaction to default to a selected O/S.

---

### Post by ajgreeny on 2023-03-03
Great news! 

Please mark as **SOLVED** from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

