---
title: "Hard Drive GParted Issue"
date: 2013-05-15
forum: Any Other OS
---

### Post by garyzaval1 on 2013-05-15
Hi, I have a IBM server x3100M4 Core i3-2100 3.1Ghz 2Gb with a SATA 1TB Simple-swap 3Gb/s Hard Drive.


I used to have vmware vsphere esxi and it worked out just fine with windows server and ubuntu server. But then i decided not to virtualize, so I tried to replace it with a install of Windows Server 2008 onto the machine.


On the windows installation I tried to format the HD and install the OS but I got this error: "windows cannot be installed on this disk. The selected disk is of the GPT partition style."
There's some information here:
[http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/windows-cannot-be-installed-on-this-disk-the/8fa72a3e-10c5-47da-a040-1e0db62af309](http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/windows-cannot-be-installed-on-this-disk-the/8fa72a3e-10c5-47da-a040-1e0db62af309)


So I tried GParted gparted-live-0.16.1-1-i486.iso booting from USB. And now it seems my HD drive is dead, GParted loads but after a while then I get this:


devd[48]: timeout: killing '/sbin/modprobe -b scsi:t-0x00'
More here: 
[http://sdrv.ms/104GsvC](http://sdrv.ms/104GsvC)
[http://sdrv.ms/181tMYl](http://sdrv.ms/181tMYl)


It keeps trying for 5 minutes like in a loop then just a black screen.


Does anyone know how to fix it?


Thanks.

---

### Post by stalkingwolf on 2013-05-15
i have had occassions that gparted on a usb wouldnt work but the live cd did.  another option is to run hirens regen.  you might also try partitioning software from the drive manufacturer.

---

### Post by oldfred on 2013-05-15
Windows only installs to gpt partitioned drives with UEFI.
       Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

If you do not have UEFI, you have to convert entire drive to MBR. And you are back to the 4 primary partition limit.
      
 To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)


 Windows convert to MBR
[http://blog.paulgu.com/2008/01/06/how-to-delete-gpt-protective-partition/](http://blog.paulgu.com/2008/01/06/how-to-delete-gpt-protective-partition/)

      
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

   Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Windows convert from gpt to MBR. Besure to have good backups - srs5694
[http://ubuntuforums.org/showthread.php?t=1718966](http://ubuntuforums.org/showthread.php?t=1718966)
Use parted or gparted to remove gpt if no data to save:
[http://ubuntuforums.org/showthread.php?t=1719851&page=2](http://ubuntuforums.org/showthread.php?t=1719851&page=2) post #20
[http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html](http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html)

---

### Post by coffeecat on 2013-05-15
Not an "Ubuntu, Linux and OS Chat" thread. Since this is a Windows installation and Gparted live CD problem...

*Thread moved to **Other OS/Distro Support**.*

---

