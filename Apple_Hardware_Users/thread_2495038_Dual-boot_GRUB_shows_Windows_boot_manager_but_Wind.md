---
title: "Dual-boot: GRUB shows Windows boot manager but Windows doesnt boot"
date: 2024-02-05
forum: Apple Hardware Users
---

### Post by x-achilles-o on 2024-02-05
Hey fellow community!

This is my first post here, Im not really new to *Ubuntu* (already use it on my old Macbook and installed *Xubuntu* years ago alongside *Windows 7*), still consider myself a rookie.

As I got my hands on a great offer - iMac 16,2 2015 with already installed *Win11* - I was eager to install Ubuntu alongside with it following the article series of the magazine c't 18/2022 where they give instructions to setup Linux alongside Windows: Windows already encrypted by BitLocker, clear up some space from the SSD for a shared safe partition and then install *Ubuntu* and encrypt it with *VeraCrypt*.
It all went fine til after the installation of *Ubuntu*: the installation process went flawless but after first start I encountered several issues. One of them is that Windows doesnt boot anymore. GRUB shows the menu entry "Windows boot manager /dev/sda1" but when I select it it only leads to a black screen and nothing happens, even after a minute waiting so the only OS bootable is Ubuntu (select it in GRUB, entering a busybox shell and encrypting sda8_crypt with ```
cryptsetup luksOpen /dev/sda8 sda8_crypt
```)
I tried fixing it by running boot-repair on Ubuntu and this is what the process summarizes:
[https://paste.ubuntu.com/p/ZBjp222dQb/](https://paste.ubuntu.com/p/ZBjp222dQb/) or
[HTML]boot-repair-4ppa2075                                              [20240204_1753]
============================= Boot Repair Summary ==============================
User choice:
Is there RAID on this computer? no

==================== blkid (filtered) before lvm activation ====================
/dev/mapper/vgubuntu-root: UUID="f5dc8cca-...-59359551ba19" BLOCK_SIZE="4096" TYPE="ext4"/dev/sdb1: LABEL="USBSAFE" UUID="5A28-EA70" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="..."/dev/mapper/vgubuntu-swap_1: UUID="a8af5fea-...-d4e8871fab6f" TYPE="swap"/dev/mapper/sda8_crypt: UUID="cmEfB3-...-JXvt-nWmnDZ" TYPE="LVM2_member"/dev/sda4: TYPE="BitLocker" PARTLABEL="Basic data partition" PARTUUID="7c425185..."/dev/sda7: UUID="cbb86dcb-...f4541" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="cea0a422-...d47"/dev/sda5: LABEL="ctRecovery" BLOCK_SIZE="512" UUID="..." TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="aa2bdf38-..."/dev/sda3: TYPE="BitLocker" PARTLABEL="Basic data partition" PARTUUID="8f03d0db-..."/dev/sda1: UUID="5A1D-58F8" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="e0259722-...-14e7b628e5c5"/dev/sda8: UUID="e4c4ea47-..." TYPE="crypto_LUKS" PARTUUID="927649fd-..."/dev/mapper/winlin-data: LABEL="winlindata" BLOCK_SIZE="512" UUID="..." TYPE="ntfs"/dev/sda2: PARTLABEL="Microsoft reserved partition" PARTUUID="2e9d0c54-..."/dev/sda6: PARTLABEL="Basic data partition" PARTUUID="bae5ac82-..."

================================ LVM activation ================================
modprobe dm-mod  vgscan --mknodes  Found volume group "vgubuntu" using metadata type lvm2vgchange -ay  2 logical volume(s) in volume group "vgubuntu" now activelvscan  ACTIVE            '/dev/vgubuntu/root' [87.89 GiB] inherit  ACTIVE            '/dev/vgubuntu/swap_1' [<8.82 GiB] inheritblkid -g



modprobe: FATAL: Module efivars not found in directory /lib/modules/6.5.0-15-genericEFI variables are not supported on this system.
Recommended repair: ____________________________________________________________
The default repair of the Boot-Repair utility will purge (in order to enable-lvm) and reinstall the grub-efi ofmapper/vgubuntu-root,using the following options:  sda7/boot sda1/boot/efiAdditional repair will be performed:  unhide-bootmenu-10s use-standard-efi-file

/dev/mapper/vgubuntu-root/boot/efi not emptyapt-get -y updatePurge the GRUB of /dev/mapper/vgubuntu-rootgrub-efi availablePaketlisten werden gelesen…Abhängigkeitsbaum wird aufgebaut…SET@_progressbar1.pulse()
Statusinformationen werden eingelesen…Die folgenden zusätzlichen Pakete werden installiert:grub-efi-amd64Die folgenden Pakete werden ENTFERNT:grub-gfxpayload-lists grub-pcDie folgenden NEUEN Pakete werden installiert:grub-efi grub-efi-amd640 aktualisiert, 2 neu installiert, 2 zu entfernen und 4 nicht aktualisiert.Es müssen 49,4 kB an Archiven heruntergeladen werden.Nach dieser Operation werden 419 kB Plattenplatz freigegeben.Holen:1 http://de.archive.ubuntu.com/ubuntu jammy-updates/main amd64 grub-efi-amd64 amd64 2.06-2ubuntu14.4 [47,1 kB]Holen:2 http://de.archive.ubuntu.com/ubuntu jammy-updates/main amd64 grub-efi amd64 2.06-2ubuntu7.2 [2.240 B]Herunterladen abgeschlossen; Nur-Herunterladen-Modus aktivDEBCHECK debOK, grub-efiDEBCHECK debOKPlease type: sudo dpkg --configure -ansudo apt-get install -fynsudo apt-get install -y lvm2nsudo apt-get purge --allow-remove-essential -y grub-com*nsudo apt-get purge --allow-remove-essential -y grub2-com*nsudo apt-get purge --allow-remove-essential -y shim-signednsudo apt-get purge --allow-remove-essential -y grub-common:*nsudo apt-get purge --allow-remove-essential -y grub2-common:*nThen type: sudo apt-get install -y grub-efi os-proberNo /dev/mapper/vgubuntu-root/etc/default/grub
Unhide GRUB boot menu in mapper/vgubuntu-root/etc/default/grub
======== Reinstall the grub-efi os-prober of /dev/mapper/vgubuntu-root =========
grub-install --versiongrub-install (GRUB) 2.06-2ubuntu7.2modprobe: FATAL: Module efivars not found in directory /lib/modules/6.5.0-15-genericmodprobe efivars
efibootmgr -v before grub installEFI variables are not supported on this system.

uname -r6.5.0-15-generic
grub-install --efi-directory=/boot/efi --target=x86_64-efiInstalling for x86_64-efi platform.grub-install: warning: EFI variables cannot be set on this system.grub-install: warning: You will have to complete the GRUB setup manually.Installation finished. No error reported.cp /boot/efi/efi/ubuntu/grubx64.efi /media/stevie/USBSAFE/EFI/ubuntu/grubx64.efidf /dev/sda1mv /boot/efi/EFI/Boot/bootx64.efi /boot/efi/EFI/Boot/bkpbootx64.eficp /boot/efi/efi/ubuntu/grubx64.efi /boot/efi/EFI/Boot/bootx64.efidf /dev/sdb1touch /media/stevie/USBSAFE/EFI/Boot/bootx64.efi.grbcp /boot/efi/efi/ubuntu/grubx64.efi /media/stevie/USBSAFE/EFI/Boot/bootx64.efi
grub-install --efi-directory=/boot/efi --target=x86_64-efiInstalling for x86_64-efi platform.grub-install: warning: EFI variables cannot be set on this system.grub-install: warning: You will have to complete the GRUB setup manually.Installation finished. No error reported.
efibootmgr -v after grub installEFI variables are not supported on this system.
Warning: NVram is locked (Ubuntu not found in efibootmgr).
update-grubSourcing file `/etc/default/grub'Sourcing file `/etc/default/grub.d/init-select.cfg'File descriptor 63 (pipe:[83117]) leaked on vgs invocation. Parent PID 37436: /usr/sbin/grub-probeFile descriptor 63 (pipe:[83117]) leaked on vgs invocation. Parent PID 37436: /usr/sbin/grub-probeFile descriptor 63 (pipe:[83117]) leaked on vgs invocation. Parent PID 37440: /usr/sbin/grub-probeFile descriptor 63 (pipe:[83117]) leaked on vgs invocation. Parent PID 37440: /usr/sbin/grub-probeFile descriptor 63 (pipe:[83117]) leaked on vgs invocation. Parent PID 37443: /usr/sbin/grub-probeFile descriptor 63 (pipe:[83117]) leaked on vgs invocation. Parent PID 37443: /usr/sbin/grub-probeFile descriptor 63 (pipe:[83117]) leaked on vgs invocation. Parent PID 37447: /usr/sbin/grub-probeFile descriptor 63 (pipe:[83117]) leaked on vgs invocation. Parent PID 37447: /usr/sbin/grub-probeFile descriptor 63 (pipe:[83117]) leaked on vgs invocation. Parent PID 37483: /usr/sbin/grub-probeFile descriptor 63 (pipe:[83117]) leaked on vgs invocation. Parent PID 37483: /usr/sbin/grub-probeFound linux image: /boot/vmlinuz-6.5.0-15-genericFound initrd image: /boot/initrd.img-6.5.0-15-genericFound linux image: /boot/vmlinuz-6.2.0-26-genericFound initrd image: /boot/initrd.img-6.2.0-26-genericFile descriptor 63 (pipe:[83117]) leaked on vgs invocation. Parent PID 38042: /usr/sbin/grub-probeFile descriptor 63 (pipe:[83117]) leaked on vgs invocation. Parent PID 38042: /usr/sbin/grub-probeFound Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Unhide GRUB boot menu in mapper/vgubuntu-root/boot/grub/grub.cfg
Bootsektor wurde erfolgreich repariert.
Locked-NVram detected. Please do not forget to make your UEFI firmware boot on the Das aktuell benutzte Betriebssystem - Ubuntu 22.04.3 LTS entry (sda1/efi/ubuntu/grubx64.efi file) !

============================ Boot Info After Repair ============================[/HTML]

As Im feeling a little frustrated from searching a solution through the internet (because I feel theres no solution or the cases not really resemble mine) and overwhelmed Im posting my problem here now hoping for individual help for my exact case. I really tried to do it on my own but now I need a little support by experienced people, at least solving one of my issues.

---

### Post by oldfred on 2024-02-05
Do not know Mac, but can you boot Windows directly from a UEFI boot menu, not grub.

Grub only boots working Windows. That also means Windows cannot be hibernated or fast boot which also sets hibernation flag nor encrypted if Windows has encrypted its ESP - efi system partition.

---

### Post by x-achilles-o on 2024-02-06
> **oldfred said:**
> Do not know Mac, but can you boot Windows directly from a UEFI boot menu, not grub.

Grub only boots working Windows. That also means Windows cannot be hibernated or fast boot which also sets hibernation flag nor encrypted if Windows has encrypted its ESP - efi system partition.
Unfortunately, no :'( when I enter UEFI there are two options: one is called WINDOWS (Im guessing its the integrated SSD) and one is an orange drive symbol called EFI boot. When I chose WINDOWS the grub menu shows with options Ubuntu, advanced options for ubuntu and Windows boot manager. When I chose EFI boot, I get the minimal bash of GRUB presented.
When I check disks via Ubuntu OS, it shows the Windows partitions, so Im confused: is Windows still there, can I "just not" enter it?

---

### Post by oldfred on 2024-02-06
With advanced options grub menu can you boot recovery mode?

I thought Mac were UEFI only, so not sure why you are getting this error?
> EFI variables are not supported on this system.

Do not know LVM either. 

You can try a full chroot. Probably some combination of UEFI & LVM mounts required.
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

### Post by x-achilles-o on 2024-02-06
> **oldfred said:**
> With advanced options grub menu can you boot recovery mode?
No, I cant, I assume due to my other problem: every time I wanna boot Ubuntu I get into a busybox shell with an initramfs prompt and need to encrypt the partition with ```
cryptsetup luksOpen
```. When I tried to start Ubuntu in recovery mode it says [HTML]Volume group vgubuntu not found... cannot process volume group vgubuntu... gave up waiting for root file szstem device... ALERT! /dev/mapper/vgubuntu-root does not exist.[/HTML]
As cryptsetup is not a built in command in this scenario I dunno how to get Ubuntu started in recovery mode.
Im getting the feeling that my problem is bigger than I thougt :(

Edit: due to a family issue I couldnt handle the issue further, still Ubuntu offered a system upgrade from 22.04. to 23.10. When the iMac starts now, no GRUB is showing, instead Im getting a window where Im asked to unlock the partition (so not booting into a busy-box shell like before). Should I still perform the suggested chroot?

---

### Post by megsoconnor on 2024-06-27
Don't be sure your problem is there but:
Be sure, for win10/11 to have in efi/bios the secure boot activated. if it resolve your windows problem it will create a linux can't boot. so you must before that to have a signed linux kernel and register it to efi/bios before activate this option.
i have the same troubles from last windows majs in Win11 at dual boot.

---

### Post by scostantino on 2024-09-04
Im new as well. Complete rookie but have Installed ubuntu years ago and now have a few out of date macs that run better with ubuntu. Im encountering pretty much the same issue.

Have a old Mac Pro (trashcan) with a "bootcamp" partition with win 11 on it. I installed Ubuntu and now Windows wont boot from Grub menu.

At first I was getting:

1.  ["Error: file '/EFI/Microsoft/Boot/bootmgfw.efi' not found"]("https://askubuntu.com/questions/1271907/dualboot-ubuntu-windows-error-file-efi-microsoft-boot-bootmgfw-efi-not-fou") which went away after I removed all external connected drives
2.  Then when I tried to enter Windows through Grub the screen would just go completely black as described in this thread 
3.  I ran disk repair And now when I select the windows option it just blinks black and back to the grub menu

Here is what I got when I ran disk repair.

============================= Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

sda2: __________________________________________________________________________

    File system:       apfs
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda2: unknown filesystem type 'apfs'.

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.


================================ 2 OS detected =================================

OS#1:   Ubuntu 22.04.4 LTS on sda5
OS#2:   Windows 10 or 11 on sda3

================================ Host/Hardware =================================

Dont want to take away from the original poster, so Ill watch from the sidelines :popcorn:and if anyone knows whats happening with mine, let me know.

Thanks in advance!

---

