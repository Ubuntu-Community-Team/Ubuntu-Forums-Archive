---
title: "Partitioning, dual boot"
date: 2013-06-26
forum: Any Other OS
---

### Post by natecgraham on 2013-06-26
Hey guys, I recently installed Linux Mint (it's a form of Ubuntu, so it's necessary to post here.. for all you possible naysayers) and I'm now running a dual boot of Linux Mint and Windows 7. I have a C and D drive on my laptop. C is for basically anything and D is strictly for my music library. I installed Linux on the C drive because it has the most space. As you all know Windows is also on the C drive. When I installed Linux Mint I only had the option to give the partition 30 GB. I've installed GParted and watched a few tutorials on it, but I'm a total newb to editing Partitions and somewhat of a newb for using Linux, though I do have some experience. Is there any "GParted for Idiots" Guide I can use to safely reduce the space on the Windows 7 partition and add space to the Linux Partition. From what I've gathered from the few tutorials I have seen, I need to make a disc of GParted and unmount the C drive. But the problem I foresee is how will I edit anything if the C drive is unmounted. Seeing as how both OS' use the C drive.  Any help would be appreciated.

---

### Post by QIII on 2013-06-26
Mint is based on Ubuntu but is a separate distro.

Moved to Other OS/Distro Support

---

### Post by oldfred on 2013-06-27
Windows tools for Windows & Linux tools for Linux.
Use Windows disk tools to shrink a NTFS partition but not change, or create partitions. It may convert to dynamic which works with nothing including many Windows repair tools.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

In Linux there is no c: drive. Drives are sda, sdb sdc etc and partitions are the number after the drive or sda1, sda2, sdb1 etc. So did you install wubi?

      
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

---

### Post by westie457 on 2013-06-27
In addition to what 'oldfred' has posted.

It looks like you have installed via WUBI.

A Wubi installation is not in its own partition, it is an area of a Windows partition set up so Windows cannot see what is inside. That is why you had the 30GB limit.

It is possible to move the Wubi installation to its own partition. See here for guidance. [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

General advice here also is to back up any and all personal files you want to keep. Just in case anything goes wrong.

---

