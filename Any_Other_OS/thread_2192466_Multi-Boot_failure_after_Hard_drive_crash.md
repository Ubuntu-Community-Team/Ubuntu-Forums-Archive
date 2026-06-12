---
title: "Multi-Boot failure after Hard drive crash"
date: 2013-12-08
forum: Any Other OS
---

### Post by jfandrews on 2013-12-08
Hello,

 I had an installed Win7, Win XP x64 and Ubuntu 10.04.4 LTS on separate drives. My first drive (Win 7 ) crashed and burned, leaving the system non-bootable. 
 I have removed the Win7 drive as it was making the system unstable, even when booting from CD. 

Note: I was going to remove Win7 anyway, so the crash just made happen sooner.

The drives on the system are dev/sda  Win7 backup
                                           dev/sdb1  Win XP Pro / sdb2 XP files
                                           dev/sdc  Win XP backup
                                           dev/sdd  CAELinux  Ubuntu 10.04.4

I have tried to use the Boot-Repair program (download from Sourceforge) to fix the bootloader, but to no avail.
The system still will not boot any OS.
On occasion it tries to boot Win7's backup drive (don't know why)

I also include a Paste from Boot-repair at [http://paste.ubuntu.com/6538411/](http://paste.ubuntu.com/6538411/)

My main goal is to get back to CEALinux and Win XP, I can work on recovering files from the crashed drive later.

My computer skills are fair, but at times....

Thank you for your help.
Jeff

[h=1][/h]

---

### Post by oldfred on 2013-12-08
Moved to OtherOS since not Ubuntu.

If you set BIOS or use one time boot key to boot the drive that is sdd, does not not boot?
If not I would use Boot-Repair to reinstall grub to sdd only. Do not use auto repair as that will reinstall grub to all MBR and you want the Windows boot loaders on your Windows drive(s). Choose Advanced, select install and select drive to install grub into. You may still have to do the full uninstall and reinstall as you show a menu.lst from grub legacy and may have mixed grub versions.
Also not sure if Boot-Repair will fully work on your 10.04.4. Desktop has been discontinued but I think server is still supported, so grub2 should still be in server repository.

Windows only boots from one partition on one drive, boot drive in BIOS and boot flag on partition. So if you install additional copies of Windows it moves all the boot files to that one partition. Your XP install has no boot files.
I would move boot files back to the XP install and use a XP disk to run repairs. Make sure boot flag is on XP partition and BIOS is set to boot from XP drive before running repairs. 
       Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 


 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)

---

