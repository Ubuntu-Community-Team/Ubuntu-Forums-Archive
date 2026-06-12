---
title: "Grub Error, no such partition grub rescue&gt;"
date: 2012-04-21
forum: Any Other OS
---

### Post by nevermindvicky on 2012-04-21
Hello All,
While I was browsing on my Windows 7 today, my system restarted itself for some reason and since then I've not been able to get into the Windows or Ubuntu for that matter.

I've followed everything possible to work around with the issue, but haven't got it fixed. I'll truly appreciate if somebody can please help me get into my system without loosing any data. Appreciate all of yours time.

Used the Windows 7 LiveCD, Ubuntu LiveCD, but haven't been able to fix it. Have also tried the bootrec.exe, and also 
```

sudo apt-get install lilo
sudo lilo -M /dev/sda/ mbr

```
Also attaching the Results.txt

>                   Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 30792 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /boot/grub/core.img /ldlinux.sys

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 4046 MB, 4046979072 bytes
25 heads, 24 sectors/track, 13173 cylinders, total 7904256 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *              8     7,904,255     7,904,248   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb2    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb3             206,848   498,463,683   498,256,836   7 NTFS / exFAT / HPFS
/dev/sdb4         598,458,368   625,140,399    26,682,032   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1DFA-2C37                              vfat       PENDRIVE
/dev/sdb2        2610C3AE10C382F3                       ntfs       System Reserved
/dev/sdb3        00C2C9E0C2C9DA54                       ntfs       
/dev/sdb4        DCC02A81C02A624E                       ntfs       RECOVERY

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)


========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Documents/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
Thanks,
V

---

### Post by cogier on 2012-04-21
I have posted this solution before but it's so good here goes again... 

There is this wonderfull tool that will sort this out for you. Go to [http://sourceforge.net/projects/boot-repair-cd/files/]("http://sourceforge.net/projects/boot-repair-cd/files/") and download the Boot Repair ISO file.

Use Brasero to "Burn an image" to CD. Then boot from the CD and when prompted use the "Fix usual problems....." option.

It's the easiest fix I have found for Grub problems.

Keep the CD in a safe place...

---

### Post by nevermindvicky on 2012-04-21
Thank you very much cogier. Can I create a usb drive instead of cd for this ? I don't have any blank cd right now with me, I need this issue fixed ASAP. Please suggest. Thx.

---

### Post by nevermindvicky on 2012-04-21
> **cogier said:**
> I have posted this solution before but it's so good here goes again... 

There is this wonderfull tool that will sort this out for you. Go to [http://sourceforge.net/projects/boot-repair-cd/files/]("http://sourceforge.net/projects/boot-repair-cd/files/") and download the Boot Repair ISO file.

Use Brasero to "Burn an image" to CD. Then boot from the CD and when prompted use the "Fix usual problems....." option.

It's the easiest fix I have found for Grub problems.

Keep the CD in a safe place...

Hello Cogier,

I ran the boot-repair and after finishing it now, I'm getting the following --
```
Boot Device not found. Please install an operating system on your hard disk.

Hard Disk (3F0).
```

Please help, this is making me nervous.

---

### Post by cogier on 2012-04-21
This does not sound too good but don't give up yet.

If you use a Live CD, can you see your Windows files on the hard drive?

If you can then I suggest you backup all the important files. You then need to reinstall the Windows MBR. Here is how to do this. [http://support.microsoft.com/kb/927392]("http://support.microsoft.com/kb/927392")

If that works and brings back Win 7 then run the repair CD again to fix Grub.

I hope this works for you but there are no guarantees.

---

### Post by nevermindvicky on 2012-04-21
> **cogier said:**
> This does not sound too good but don't give up yet.

If you use a Live CD, can you see your Windows files on the hard drive?

If you can then I suggest you backup all the important files. You then need to reinstall the Windows MBR. Here is how to do this. [http://support.microsoft.com/kb/927392]("http://support.microsoft.com/kb/927392")

If that works and brings back Win 7 then run the repair CD again to fix Grub.

I hope this works for you but there are no guarantees.

Thanks again for your reply. When I boot using my Windows Installation disk, it can identify an existing Windows 7 installation, but as soon as I take the cd out and start it using my HD I get the same error. Don't know what are the options, but I need to preserve all my data. God help me now. Please let me know if you have any suggestions. Thanks.

---

### Post by westie457 on 2012-04-21
Hi, a couple of options.

1, Run 'testdisk' while using a LiveCD in try mode to repair the partition table.

Testdisk is available in the repositories or available with full instructions here
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)


2, Is fixparts, available here
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by nevermindvicky on 2012-04-21
Thank GOD, one good thing I still all of my data in there. So, the next thing I'm gonna do is export them to a hard drive and save them there. Then I need to find a way to restore my installation. I don't want to go to the level of re-installing everything again. Hoping I'll be able to manage that.

---

### Post by nevermindvicky on 2012-04-21
> **westie457 said:**
> Hi, a couple of options.

1, Run 'testdisk' while using a LiveCD in try mode to repair the partition table.

Testdisk is available in the repositories or available with full instructions here
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)


2, Is fixparts, available here
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Thanks westie, I'll explore these options, but first thing I need to backup everything while i can. I appreciate everyone of yours help. Just hoping I can come out winner with yall's help. Thanks.

---

### Post by oldfred on 2012-04-21
Moved to other OS. Since it is only Windows.


Your flash drive is promoted to sda. So when you installed lilo to sda you actually installed it to your flash drive not your hard drive.
Some BIOS seem to promote external devices to sda where most systems add it to the end of the list of hard drives. 

Although I just changed to use AHCI and now a flash drive may be anywhere on the list of drives. So I have to pay attention to which drive is which.

If you remove flash drive can you boot? You still show Windows boot loader in MBR of your hard drive.

---

### Post by nevermindvicky on 2012-04-21
> **oldfred said:**
> Moved to other OS. Since it is only Windows.


Your flash drive is promoted to sda. So when you installed lilo to sda you actually installed it to your flash drive not your hard drive.
Some BIOS seem to promote external devices to sda where most systems add it to the end of the list of hard drives. 

Although I just changed to use AHCI and now a flash drive may be anywhere on the list of drives. So I have to pay attention to which drive is which.

If you remove flash drive can you boot? You still show Windows boot loader in MBR of your hard drive.

Hello oldfred, Thanks for your reply. I'm able boot w/o Flash drive, but that Error has started appearing again. ```
Grub Error, no such partition grub rescue>
``` Can you suggest how should I go about it ? Thanks.

---

### Post by oldfred on 2012-04-21
You have no Linux install, just Windows, so a grub boot loader in the MBR has nothing to jump to, to continue to boot. You have to install the Windows boot loader, lilo or other Windows work-alike boot loader to boot your Windows install.

If you did have Linux, then go back to    	nevermindvicky's post on testdisk to see if you can recover it.

---

### Post by nevermindvicky on 2012-04-21
> **oldfred said:**
> You have no Linux install, just Windows, so a grub boot loader in the MBR has nothing to jump to, to continue to boot. You have to install the Windows boot loader, lilo or other Windows work-alike boot loader to boot your Windows install.

If you did have Linux, then go back to    	nevermindvicky's post on testdisk to see if you can recover it.

I did have an installation of Ubuntu, so I guess I need to delve into testdisk.

---

### Post by nevermindvicky on 2012-04-22
> **westie457 said:**
> Hi, a couple of options.

1, Run 'testdisk' while using a LiveCD in try mode to repair the partition table.

Testdisk is available in the repositories or available with full instructions here
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)


2, Is fixparts, available here
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Westie, can you please tell me the steps I can use to run testdisk from live cd of Ubuntu. Thx.

---

### Post by oldfred on 2012-04-22
Some links here:

repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[]("http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS")

---

### Post by nevermindvicky on 2012-04-22
> **oldfred said:**
> Some links here:

repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[]("http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS")

Hello oldfred,
Thank you very much for your attention. I tried all that and after writing my partition table again, I rebooted my machine, and now I see a message ```
BOOTMGR is missing. Press Ctrl + Alt + Del to restart.
``` When I reboot and try to boot from DVD,it doesn't let me get to the BIOS options. Please help me get my system working again. I know that all of my data and my OS is still there, just need to find the way to get it working. Please help this desperate person. Thx.

[EDIT]-- Please ignore my message. I'm able to boot into my Windows now, had to copy the bootmgr from Windows DVD to the C: drive to get it back in healthy shape. Hope it will be fine from now on. If I see any other issue again, will get back to this wonderful forum of such knowledgeable and helpful people. Can't thank you enough people.

---

### Post by oldfred on 2012-04-22
Glad you got it working. May be best to have good backups before starting next time. And a repair CD or USB, if you cannot start DVD in repair mode.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

