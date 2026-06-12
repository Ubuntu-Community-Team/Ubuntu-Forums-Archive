---
title: "ubuntu installation doesn't detect windows 8"
date: 2013-03-05
forum: Any Other OS
---

### Post by MrsChips on 2013-03-05
Hello,

I've done a lot of searching for an explanation to this. I have a new computer with windows 8 pre-installed. this was my procedure;

partition hard drive from windows 8 to make room for ubuntu
burn ubuntu 12.04.2 64bit (this should have uefi support) to CD
disable secure boot
boot from cd in uefi mode

now i get the normal installation interface however then i get the option to either erase hard disk and install ubuntu or manuallly partition the drive, but no option to install ubuntu alongside windows 8 as win8 has not been detected. Would it be alright to just manually partition the drive despite the current OS not being detected, or would there be problems later? is this something to do with the efi system partition? Maybe i should try ubuntu 12.10?

I'm a noob btw!

Any help/guidance would be really helpful!

---

### Post by flipflip47 on 2013-04-13
I too am having issues with installing Ubuntu alongside windows 8.  I am experiencing the same issues as you are.  No option to install alongside windows 8 as it does not detect it.  I tried to follow the steps in other threads to no avail.  My computer is a HP Envy h8-1414 desktop.  I am not sure if its because I have 4 partitions or what, but I have given up on trying to install Ubuntu for now as it has become too annoying.  I am going to wait for the next version of Ubuntu to see if it will detect windows 8 and install on its own.

My mistake, it has five partitions on it, and it is gpt partition.  Not sure if your partitions are gpt as well.

---

### Post by abovett on 2013-07-17
Hi

I've just tried to install Ubuntu 13.04 alongside Windows 8 on a Dell Inspiron 15R and run into the same problem - the installer doesn't detect Windows. It says it has not detected another installed OS. If I boot to the Ubuntu desktop, I can see the partitions on the hard disk but the installer is failing to recognise the partition to boot from. The partition layout loks rather more complex than I'm used to:

1: ESP - 524MB - "EFI system" - FAT
2: DIAGS - 42MB - FAT
3: Microsoft Reserved - 134MB - unknown partition type
4: WINRETOO... - 524MB - "Microsoft Windows Recovery Environment" - NTFS
5: OS - 986GB - "Basic Data" - NTFS
6: PBR Image - 13GB - "Microsoft Windows Recovery Environment" - NTFS

I'm booting in UEFI mode so I assume this must be GPT partitioning.

It appears that partition 5 is the main Windows/data partition, but it's not being recognised. I've tried turning Secure Boot off but (unsurprisingly) it makes no difference - the problem is not booting (the USB flash drive with Ubuntu on it boots just fine) but recognising Windows.

I need to be able to boot both Wiondows 8 and Ubuntu on this laptop, so help would be much appreciated.

Regards

Andy

---

### Post by oldfred on 2013-07-17
Your Windows partitions do not look like they are in the correct order? System reserved must be just before Main Install.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

Make a full backup of Windows and of the efi partition. And make a Windows repair flash drive.
      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Then use Windows own disk tools to shrink the main Windows partition and reboot so it can run chkdsk.
Make sure fast boot is off and check to see if Windows boots with secure boot off or not. Some do and some do not. If secure boot is required you will need the UEFI version of grub with Microsoft signed shim and signed kernels.

See also my signature.

Some other models of Dell that may be similar?

 Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)
Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
Do not understand why flash cache is required, just install to SSD?
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

 Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

---

### Post by abovett on 2013-07-18
Hello, and thanks for your advice oldfred.

By the time I read this I had already found a solution (maybe not the best one)  in these posts:

[https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Thecore of it was to resize the Windows from within Windows, install in the free space (ignoring the fact that the Ubuntu installer can't see Windows), and then install and run boot-repair. Maybe there was abetter, cleaner way, but I have Windows and Ubuntu both running now.

> **oldfred said:**
> Your Windows partitions do not look like they are in the correct order? System reserved must be just before Main Install.

The partition order was as the machine came, pre-installed with Windows 8 by Dell. It seems to work and as I don't yet know much about GPT and UEFI I'd rather not mess around too much and risk trashing the system. I will review  the links you provided to learn more, though - thanks.

Regards

Andy

---

