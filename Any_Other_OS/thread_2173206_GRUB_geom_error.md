---
title: "GRUB geom error"
date: 2013-09-08
forum: Any Other OS
---

### Post by ankit3 on 2013-09-08
[FONT=arial]Hi,[/FONT][FONT=arial]
[/FONT]
[FONT=arial]I recently installed caelinux (based on ubuntu 10.04.3) alongside an already existing Windows 7 installation and I have since not been able to boot either of the OSs. I get a grub geom error. I ran a bootinfo script and the results are at the following locations:[/FONT]
[FONT=arial][http://paste.debian.net/37041/](http://paste.debian.net/37041/)
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I'd like to mention that I have 2 harddisks (1 ssd and a hdd) controlled by a Dell H310 Perc controller. I am a novice in these areas and I would really appreciate some advice on how to tackle this issue. 

Thanks,
Ankit[/FONT]

---

### Post by oldfred on 2013-09-08
Moved to OtherOS.

I would install Windows boot loader to sda and grub to sdb. Do not use auto repair as that will just install grub everywhere. You can uncheck auto, check update MBR and in Advanced choose which system to which MBR.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by ankit3 on 2013-09-09
Thanks a lot oldfred. I had used bootrepair yesterday but had used the auto-repair function and it did not make any difference. However, as you advised, I used the restore MBR functionality and now my Windows 7 comes up! This is a huge relief. Given the fact that I have a dual hard-disk system with the RAID controller, is there a reasonable way to setup dual boot. While installing ubuntu I just followed the steps and it messed up the MBR and I am not sure why it happened. Thanks a lot again.

---

### Post by oldfred on 2013-09-09
If you have two drives and not using RAID, then you should have BIOS in AHCI mode, not RAID, nor IDE.
Some Windows may not have AHCI drivers and need those to be installed before change in BIOS. If Windows boots after change then you have drivers.

---

