---
title: "Boot issues when using boot-repair"
date: 2014-05-19
forum: Any Other OS
---

### Post by gunmastertex3 on 2014-05-19
I ran the recommended settings for the boot-repair tool when I  was trying to link my windows 7 and Ubuntu that were on separate  drives. Now my windows will not start as I get the error code  0xc0000098. 


  I noticed that there is within my boot folder in Ubuntu, an efi folder that contains a windows EFI boot manager. How do I  remove this and repoint Windows boot manager to the boot magager on my windows drive?

---

### Post by oldfred on 2014-05-19
Do not run Boot-Repair's auto fix as that just installs grub to every MBR. Use advanced setting and choose each system and which drive.

But are both systems installed in BIOS or both in UEFI boot mode?
Most Windows 7 systems are installed in BIOS mode, but a few are UEFI. Standard DVD install of Windows 7 is BIOS only, you have to convert to flash drive and update to be a UEFI install.

Post link to BootInfo report from Boot-Repair.

---

### Post by gunmastertex3 on 2014-05-19
Here is the link to the boot-repair boot info

[http://paste.ubuntu.com/7489394/](http://paste.ubuntu.com/7489394/)

---

### Post by oldfred on 2014-05-19
You have two gpt partitioned drive sda & sdb. And Windows is installed on sda. Windows only boots from gpt partitioned drives with UEFI.
Your sdc drive is MBR(msdos) partitioned. Both Windows & Ubuntu only boot in CSM(BIOS) boot mode from MBR drives.

You cannot dual boot from grub menu when systems are not in same boot mode. You should be able to boot from UEFI menu with CSM/BIOS on to boot Ubuntu or UEFI on to boot Windows. Some auto switch so you do not have to change settings, but can only boot from UEFI menu.

May be best to reinstall Ubuntu in UEFI mode. But I would install an efi partition on the sdc drive so It can boot without any other drive.

 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---

### Post by gunmastertex3 on 2014-05-19
Thanks for the help, but what do I do about my windows? It will not boot at all, even from the windows boot manager. Or will redoing the Ubuntu solve that issue?

---

### Post by oldfred on 2014-05-19
You may have to go into UEFI/BIOS and turn on UEFI. Then choose Windows from that.

For whatever reason Boot-Repair did put a Windows boot loader in the MBR for BIOS boot, but that will not work.
You need to consistent boot in UEFI mode not BIOS boot mode.

Any other Windows issues would need a Windows repair CD or Flash drive to fix. Nothing major looks out of place, but Boot-Repair or any Linux tools can only do minor repairs to Windows.

Not sure if Windows 7 in UEFI mode needs same type of repair flash drive as Windows 8 or not.
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

