---
title: "Help - Windows 8 won boot - working through Ubuntu."
date: 2013-05-14
forum: Any Other OS
---

### Post by zerowalker on 2013-05-14
Okay so i was going to install windows xp on another harddriver then my primary OS Windows 8.
So i turned off the PC through Windows 8, which seems to really put it in hibernation, which i didn know.

Then after windows xp was installing, i couldn boot into anything, except my Ubuntu that i had on another drive.
I tried to fix the boot through windows 8 installation/rescue disk, but nothing works, it seems that the drive is locked thanks to the hibernation.

So now i am in Ubuntu, and i can acess the driver through a command, it mounts it as /media, and i don really know what to do from here.

Should i delete the hibernation file to repair the Bootmanager, or what can i do?

Help appreciated ASAP.

Many Thanks!

---

### Post by oldfred on 2013-05-14
Moved to Other OS

You may do better on a Windows forum.
 [http://www.eightforums.com/](http://www.eightforums.com/)

I do not know if any of these discuss your issue or not.

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

While discussing Vista, it applies to all Windows.

 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by zerowalker on 2013-05-14
Okay i solved it, partly. I can boot into Windows 8.

But, when i try to make a bootmanager on the same drive as Windows 8, it breaks.

I used Testdisk to look up what breaks, and it seems that partitions overlap each other.

Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P Sys=72               119528  74  3 232582  38 44 1816210284

Bad relative sector.
 2 * Sys=6C               120512  46 15 242121 118  1 1953653108

Bad relative sector.
Space conflict between the following two partitions
 1 P Sys=72               119528  74  3 232582  38 44 1816210284
 2 * Sys=6C               120512  46 15 242121 118  1 1953653108



I have no idea what to do:(

---

### Post by oldfred on 2013-05-14
Is this pre-installed Windows with UEFI and gpt partitioning. Or your install and using BIOS and MBR partitioning.

If MBR:
 Fix overlaping partition error srs5694 Post #34
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print
sudo sfdisk -l -uS

 First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt



IF gpt:
sudo gdisk -l /dev/sda

---

### Post by zerowalker on 2013-05-14
It´s Bios with MBR.

Can it be fixed through Testdisk?

---

### Post by oldfred on 2013-05-14
Possibly.
The issue becomes do you have any data in the overlap area and then which partition does it belong to. Often partitions are written into more at the front, so that may be the best choice, but no guarantees. If you have not backed up your data, be sure to do that before anything else.

Testdisk usually shows all the alternatives that existed if you changed partitions. You have to select a set that does not overlap, not some combination of old and new that may overlap.

---

### Post by zerowalker on 2013-05-14
I think 6C is the problem maker, it may occur cause that i extended the windows partition earlier with the "system reserved" partition, as i didn´t need it.
And windows didn´t allow it, so i did it out of windows.

So when i now write a boot manager with easybcd (so i can have many OSes), it breaks and writes on top of each other.

But how can i solve it, can i remove 6C?
Cause i can´t find a way to do it, just to analyse and find lost partitions which doesn´t really help me.

Thanks

---

### Post by oldfred on 2013-05-15
Testdisk still uses the ancient CHS cylinders, heads, sectors which I last used 15 years ago.

I understand fdisk, or parted as they work in sectors and all drives now use LBA or AHCI which are sector based.

Post this
sudo fdisk -lu

 Testdisk uses CHS - formula for conversion to LBA
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

---

### Post by zerowalker on 2013-05-15
Ah, didn´t know that.

But i kind of solved it.
Or half the problem, the problem only occurs with the program.

I am wondering, can i install another bootmanager, maybe linux based (grub i think it´s called), that let me choose from my OSes (Got W8, XP and Ubuntu), and that i can install on my C: Drive (My SSD)?


EDIT:

I think it may have to do that windows doesn´t seem to know that the harddrive has a partition.

In diskpart, if i list partitions, it says Partition 1, but i can´t select it.

I don´t know if it´s possible to remake the partition somehow, maybe using fdisk in ubuntu without erasing data on the drive.

---

### Post by oldfred on 2013-05-15
If it is just the partition type and not the format, you can use disk utility and just change the type. That just changes the partition table entry and how the system will read the partition, so if not correct type it will not work. But if type got changed somehow that can fix it. Otherwise you have to reformat which will erase data.
Often deep search in testdisk will find data and let you copy it. Or part of testdisk is another program photorec which just scans drive for anything that looks like a file.

 I have used photorec, it is slow, needs lots of room to copy files to another drive and only finds files by type or extension as file name is not available. It also finds deleted files as I had saved some text files many times & it found most of them and I had to do a lot of file compares to see if one had more data than another.

---

### Post by zerowalker on 2013-05-15
I see, well it isn´t from format.

I will try to make a Grub boot loader instead of using a windows based one.
Perhaps that will solve my problems.

---

### Post by oldfred on 2013-05-15
Best to post Boot-Info report.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If you resized a NTFS partition you need to run chkdsk on it. It has internal data that must match partition table & chkdsk updates that.

---

### Post by zerowalker on 2013-05-15
Well i used it, it didn´t work as intended though. I needed to make a grub_bios partition, so i couldn´t install it on the Windows partition.
And The windows appeared as unallocated space.

But i was able to make a test, and get Ubuntu to work, and boot into the other boot manager i use currently.
But it didn´t solve anything really, except that Ubuntu worked.

I think i have really messes up so i can´t boot from my Windows, but i guess i can live with that, doesn´t really hurt anything i guess, as i can get into everything anyway.

---

### Post by oldfred on 2013-05-15
If Ubuntu insisted on a bios_grub partition, you are installing in BIOS mode on a gpt partitioned drive. Windows XP cannot read gpt partitioned drives.
I have gpt on several drives booting with BIOS and have the bios_grub. And I still have but do not use now my XP install on sda. I used to be able to dual boot without issue, other than XP not seeing gpt drive.

---

### Post by zerowalker on 2013-05-15
Yeah seems so, i think it´s the Ubuntu drive that´s gpt.
I will have to fix it up sooner or later.

But is there a way to clean all boot files from the drives?
Cause i think i messed up while playing around, so i think some drives have boot files that can´t be used etc.

---

### Post by oldfred on 2013-05-15
Post BootInfo report from Boot-Repair. Then we can see details.

---

### Post by zerowalker on 2013-05-17
[http://paste.ubuntu.com/5675766](http://paste.ubuntu.com/5675766)

Hope this is correct.

---

### Post by William D. on 2013-05-17
This is what I did and it works just fine no problems at all.  I installed Windows 8 on a SSD. Got it working the way I wanted. Then turned off the computer, disconnected the SSD.  Installed a Second SATA Hard Drive (not SSD) and Installed Windows 7.  Disconnected that Hard Drive and Installed a Third Hard Drive and Installed Ubuntu.  Turned off the computer are reconnected all three Hard Drives.

DID NOT install a boot loader.  No need.

When I turn on the Computer, I press the F12 Key and a menu comes up listing all the drives.  I just select which HD to boot off of.   Works great.    Gigabyte MotherBoard, Intel Chipset, I7 processor.

---

### Post by zerowalker on 2013-05-17
But i do not really have problem with the booting itself.
I have problem getting the boot loader to work on the SSD.

I want to have a boot manager on the SSD that let´s me choose from Windows 8 (on the SSD) and my other OSes on other HDDs.
It can be a Windows 8 Boot Loader, or GRUB, i don´t really care, as long as it´s working (and is not slow or something).

---

### Post by oldfred on 2013-05-17
I used to boot my sda XP from my gpt drive on sdb.

So from current grub, cannot you boot all your installs? IF you set sdc as default.

Which drive do you want to boot from.
You can install grub to any MBR from you install if you want, but I prefer each system have its boot loader in the MBR of the drive with the install. Then when a drive fails you can boot another drive from BIOS or one time boot key as William D. does. It just is I normally use grub menu to boot and only do it that way in  an emergency.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

You can change sdb to any drive. I boot several installs in sdc from MBR in sda & sdb. My BIOS is set to default to sdd which is my SSD.

---

### Post by zerowalker on 2013-05-18
I want to boot from my SSD.
But i can´t do it with that i think, as the Drive isn´t detected as a working drive, it´s detected as if nothing was written to it.
I read that the problem seem to occur when windows is hibernated, but i have disabled that in windows 8 and Fast Startup, but still i get the problem.

---

### Post by oldfred on 2013-05-18
Because of the way Windows 8 works it is difficult to dual boot when hibernated. I would just leave that drive as Windows. And boot with grub on the Ubuntu drive when you want it.
You can use your one time boot key to change which device to boot from which is not too difficult to do.

Even if dual booting with multiple Windows you have to be careful with your Windows 8 partition.
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
[http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by zerowalker on 2013-05-18
The problem is thay i have it disabled. I can live without hibernation.

But it doesn´t seem to solve it.

And i can´t boot into windows 8 from the SSD, i have to use a boot manager on another drive.
Cause if i install or repair the boot manager on the SSD, the NTFS boot sector get´s corrupted.
That´s why i want Grub on the SSD, as it maybe doesn´t corrupt the boot sector.

Else i have to live with it until i reformat.

---

### Post by oldfred on 2013-05-18
When you installed Windows did you let it see your other installs. Windows can only boot from one drive set as boot drive in BIOS and only from one partition on that drive. In Windows it is the active partition and we just see the boot flag in Linux.
So if you installed another Windows to a second drive while another drive was boot drive in BIOS, Windows will install its boot files into that drive & boot partition. You should be able to move boot files & run repairs to get boot files in same drive as install.

 To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words Vista but applies to all BIOS/MBR Windows systems, but not UEFI.
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by zerowalker on 2013-05-18
The problem is.

I can´t repair the boot manager/files on the SSD to let it boot from there.
I can only boot into windows 8 if i have the boot manager on another drive.

If i repair the SSD boot manager, or install it there, the Boot Sector get´s corrupted, and i have to repair it, reverting the change.
I can´t see the boot flag in linux either, as it just get´s detected as an Unallocated partition in Gparted, else i could have played around and perhaps have solved it.
As windows is quite limited when it comes to repairing and installing boot files.

---

### Post by oldfred on 2013-05-18
Did the Boot-Repair BootInfo report show the SSD? It should show every drive that BIOS reports.
What mode do you have BIOS in? - AHCI, LBA or something else. AHCI is preferred for new systems and SSDs so trim will work, but I know with Windows 7 you had to add drivers before changing. And XP will not work with AHCI.

---

### Post by zerowalker on 2013-05-18
It should, it´s 500gb.

I have in AHCI and Trim and everything works correctly.

As said, i think the boot sector get´s corrupted thanks to me extending the partition over the "System Reserved", and Windows doesn´t know how to work with that.
So that´s why i though Linux might be able to make a boot loader on it without the problem Windows has.

---

### Post by oldfred on 2013-05-18
The grub boot loader just chain loads to Windows PBR or partition boot sector. All it does is skip the MBR which really just chain loads to the PBR with the boot flag whether it has boot files or not. Where grub will not chain load unless it has found the boot files and does not care about boot flags.

If Windows is corrupted you need to repair it first. Often chkdsk will fix up a PBR that is broken. A PBR has to have the same type of info on start sector and size of the NTFS partition as the partition table. If not it will not boot. And the PBR has to have the correct Windows boot files.

 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by zerowalker on 2013-05-18
I see, then maybe it won´t work.

Cause, it doesn´t matter if the windows is corrupted or not.
If it´s not corrupted (like now), i can boot into windows 8, ONLY by using a boot loader on another drive.
If i try to load into the SSD directly (through bios) it won´t load, which is understandable, as it doesn´t have a boot loader, only windows itself.

So if i then install the boot loader on the SSD. Well then it get´s corrupted.
And if i repair it, it removes the boot loader and files, so i have to reinstall it, and have the boot loader, once again, on another drive.

It´s very weird.

---

### Post by oldfred on 2013-05-18
You can often move boot files, boot flag and Windows boot loader in MBR without reinstalling by moving files and running repairs from Windows repairCD or USB.

---

