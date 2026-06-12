---
title: "GRUB not detecting Windows 7 (surprise!)"
date: 2012-10-12
forum: Any Other OS
---

### Post by kipjones on 2012-10-12
BOOOOORING, I know!  But I'm ONE MORE guy who can't quite figure out how to boot my win7 partition.  It's been two months now and I have to get back in there for some proprietary stuff that just doesn't work in wine.  

I can mount the partition, access the files, but os-prober just will not see it.  I'm scared to even place the windows restore CD in my optical drive, because Precise is running oh-so-nicely and I don't want to screw it all up!

The output of sudo fdisk -l:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07f2837e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   de  Dell Utility
/dev/sda2          208896    41172991    20482048   83  Linux
/dev/sda3   *    41172992   216954241    87890625    7  HPFS/NTFS/exFAT
/dev/sda4       216954878   976771071   379908097    5  Extended
/dev/sda5       216954880   951328767   367186944   83  Linux
/dev/sda6       951330816   964028415     6348800   82  Linux swap / Solaris
/dev/sda7       964030464   976771071     6370304   82  Linux swap / Solaris

```my bootinfo URL:  [http://paste.ubuntu.com/1276068/](http://paste.ubuntu.com/1276068/)

What should I do?  Try the windows CD and hope for the best?  Is it possible the problem is in the VBR of /dev/sda3?  If so, how can I replace just that?

Cheers, thanks for taking the time to help aNOTHER guy through this common stumbling block.

-Kip

---

### Post by oldfred on 2012-10-12
Moved to other OS as it really is a Windows repair issue.

It probably is fixable, but you over wrote the Windows boot partition. Normal installs of Windows 7 have a hidden 100MB boot/repair partition and the main install. You are missing two key boot files.

Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=Red]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

You are missing bootmgr & the BCD. I did see one user who just copied bootmgr & the BCD into his system from his repairCD. But of course he then had to edit the BCD as the defaults were the repair not the install.

For Windows repair to work you also need the boot flag (in Windows make active) on your sda3. It  was on the now missing Windows boot partition. Windows will only repair the boot of the partition with the boot flag. And that partition has to be formated NTFS and a primary partition (which yours is). 

You do have a Windows repairCD or USB? You need a current version repairCD or Linux liveCD for every operating system you have installed. If you have access to another Windows 7 same 64 or 32 bit version you can make a repair CD.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

---

