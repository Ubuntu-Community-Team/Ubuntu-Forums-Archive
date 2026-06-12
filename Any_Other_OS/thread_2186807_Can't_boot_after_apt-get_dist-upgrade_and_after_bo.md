---
title: "Can't boot after apt-get dist-upgrade and after boot-repair =&gt; going EFI shell prompt"
date: 2013-11-09
forum: Any Other OS
---

### Post by dche on 2013-11-09
Hello Guys,

I have an issue with boot: I am going to EFI shell prompt when booting with 
no escape to my Linux Mint 15 installed. I am stuck.
Let me give you the background:

I am using a PC with UEFI booting, the installation of Linux Mint 15 from scratch was done a few weeks ago 
without problem on my SSD drive located in /dev/sda
They are 2 partitions: sda1 for the /boot/efi, and sda2 for Kernel. GPT partition on sda.
All was done smoothly without user intervention, all automaticaly.

The issue came when I decided to upgrade my Linux with "apt-get dist-upgrade" ,
I had some dependencies issue, and thought it could be a good idea at that time, 
I realised then it was actually installing a new kernel, yeah dist-upgrade I realized :oops:... the French MANUAL was not clear enough for me, 
I was prompted to choose the place for Grub, I have had chosen /dev/sda.
After that I am falling to EFI prompt shell at every boot.
As I did not change anything in the PC BIOS to boot to my SSD, I don't think the issue is in BIOS boot config.
I thought it was more a GRUB issue, I wanted to understand before touching to the system so I execute boot-info
I had this output (FYI: /dev/sdb is my data disk with label BigData that used to have a bootable partition, /dev/sdc is my Mint Live DVD USB Key to execute the repair)
    
:

[FONT=courier new]                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    113835496 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        /efi/linuxmint/grubx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 15 Olivia
    Boot files:        /boot/grub/grub.cfg /etc/fstab
    
    [/FONT]
    

For me the issue was more on the MBR,
I decided to re-install GRUB on /dev/sda with that method (comments in French , coming from [http://doc.ubuntu-fr.org/tutoriel/comment_restaurer_grub):](http://doc.ubuntu-fr.org/tutoriel/comment_restaurer_grub):)


[FONT=courier new]sudo fdisk -l                      # pour vous aider à trouver la partition sur laquelle est votre ubuntu
sudo mount /dev/sdaX /mnt          # montage de celle-ci en remplaçant le X par le bon numéro de partition
sudo mount --bind /dev /mnt/dev    # lien symbolique du dossier /dev en cours d'utilisation vers le disque monté
sudo mount --bind /dev/pts /mnt/dev/pts   # lien symbolique du dossier /dev/pts en cours d'utilisation vers le disque monté
sudo mount --bind /sys /mnt/sys    # lien symbolique du dossier /sys en cours d'utilisation vers le disque monté
sudo mount -t proc /proc /mnt/proc # Pour que Grub2 trouve /proc/mounts
sudo chroot /mnt /bin/bash         # mise à la racine du disque monté
mount -a                           # montage des partitions dans le chroot
[/FONT]
=> I did not execute the 2 next lines, first because in my case that would be more "apt-get install grub-efi"
=> and because all looked fine from what I understood from the boot-info
[FONT=courier new]apt-get install grub-pc            # installation du logiciel Grub2 (sur le disque maintenant à la racine)
update-grub                        # création d'un nouveau fichier de configuration : grub.cfg
[/FONT]
=> I executed the next lines

[FONT=courier new]grub-install /dev/sda              # installation de grub sur le MBR[/FONT]
[FONT=courier new]umount -a
exit  (to go out from root /bin/bash triggered by "sudo chroot /mnt /bin/bash" above, 7th command)
sudo umount /mnt/{dev/pts,dev,sys,proc}
sudo umount /mnt[/FONT]

Then reboot
=> Same issue , going to EFI shell prompt  when booting


Then I have decided for a boot-repair execution:
=> Same issue 
=> Output of  boot-repair :  [http://paste.ubuntu.com/6386971/](http://paste.ubuntu.com/6386971/)

[B]Could you tell me from which part the issue is coming ? And how to solve it?

You help and your time would greatly appreciated. Thank you.

[/B]
David

---

### Post by dche on 2013-11-09
Hi 
I have found a workaround:

I have created the file: /boot/efi/startup.nsh with that content:

fs0:\EFI\linuxmint\grubx64.efi

So I can boot with my latest kernel 3.8.0-32, the one installed by dist-upgrade. BUT I go through the EFI Yellow prompt waiting for any interruption before executing startup.nsh
THEN I wait again on the Grub prompt/menu for choosing the kernel (new one, previous one, setup)

So boot time is much longer and I really don't need to go through all these new steps.

Why did not I go through all these steps at the first Linux Mint 15 installation? 
Does it mean I was not really using UEFI? And I was booting directly with MBR to Linux Kernel? 

Your comments and guidance is welcomed

David

---

### Post by dche on 2013-11-13
It is solved, I am not going through the EFI Shell Prompt, it goes directly to the Grub menu.

To recall my sda disk on which I boot:

[FONT=courier new](parted) print
Model: ATA OCZ-AGILITY3 (scsi)
Disk /dev/sda: 90,0GB
Sector size (logical/physical): 512B/512B
Partition Table: [COLOR=#ff0000]**gpt**[/COLOR]

Number  Start   End     Size    File system     Name  Flags
** 1      1049kB  99,6MB  98,6MB  fat32                 boot**
 2      99,6MB  82,3GB  82,2GB  ext4
 3      82,3GB  90,0GB  7733MB  linux-swap(v1)[/FONT]

sda1 is the EFI partition, mounted on /boot/efi:

[FONT=courier new]ilesystem      1K-blocks      Used Available Use% Mounted on
**/dev/sda2        78876576  47126256  27736908  63% /**
none                    4         0         4   0% /sys/fs/cgroup
udev              3627048         4   3627044   1% /dev
tmpfs             3644268         8   3644260   1% /tmp
tmpfs              728856      1040    727816   1% /run
none                 5120         0      5120   0% /run/lock
none              3644268        80   3644188   1% /run/shm
none               102400        20    102380   1% /run/user
tmpfs             3644268         0   3644268   0% /var/tmp
tmpfs             3644268         0   3644268   0% /var/spool
tmpfs             3644268     81768   3562500   3% /var/cache
/dev/sdb1      1442014140 387995024 980762316  29% /media/BigData
**/dev/sda1           94759       241     94519   1% /boot/efi**[/FONT]

on that sda1 partition I have created the file: **EFI/boot/bootx64.efi**   which is a copy of **EFI/linuxmint/grubx64.efi**
That way my PC executes directly the Grub menu without going through the yellow EFI prompt.

I have found the solution here: [https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

