---
title: "GRUB loading forever - can't boot at all"
date: 2014-06-17
forum: Any Other OS
---

### Post by frederik-f on 2014-06-17
Hi guys.

I have Windows 8 and installed Ubuntu 13.04 as a dual boot. Had a lot of problems with installing it, because the bootloader never saw Ubuntu, but the wupi helped with that.

I recently installed Kali Linux (For learning puposes of course), and it worked perfectly the first time. And the second time when I decided to boot to Windows, it worked perfectly too.

But I then rebooted and was stuck with 'GRUB loading...'. I have been waiting for more than 30 minutes, but nothing happends. I went to my Ubuntu live CD, and installed Boot-repair. But the boot-repair failed to reapair. I got following from the boot-repair: [http://paste.ubuntu.com/7659892/](http://paste.ubuntu.com/7659892/) . I know my PC is messed up because of several Ubuntu installation attempts. 

I'm know stucked with the live CD, and my only wish is to get be able to use Windows again. When I have Windows, I will be able to figure out, how to install Ubuntu again. I don't need Kali Linux.

Is it possible to remove the Kali linux which kaused the problem, or remove both of my linux distros?

---

### Post by oldfred on 2014-06-17
You converted your Windows to SFS or dynamic partitions. That does not work with Linux and does not even work with some Windows repair tools.

Microsoft has no undo, just full backup of everything (which you should do anyway) and erase drive and repartition. The dynamic partitioning is a proprietary Windows way to work around the 4 primary partition limit.
Everyone else uses an extended partition (one of the 4 primary) which can hold an unlimited number of logical partitions.

       Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
 Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)



You also show a wubi install. best to just use second drive as a Linux drive and keep first drive as Windows drive.
      
 Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by frederik-f on 2014-06-18
Thank you very much! So what you are telling me is:

1. Backup everything
2. Format my Hard drive

I am not able to access my Windows partition. I tried to folllow this tutorial: [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/) , but the tutorial does not cover the SFS format. Is it possible to backup my data when I have SFS, or am I forced to format my Hard drive without a backup?

---

### Post by oldfred on 2014-06-18
The third party partition tools Easus or Mini-Tool should also mount your dynamic partitions. 

Never actually used them, but they may fix your Windows also as they include many other Windows fixes also.
I would try them first.

---

### Post by frederik-f on 2014-06-19
But the problem is just that both of the tools are Windows tools, and I am not able to access Windows. 

It would maybe just be better to delete the GRUB2 and use Windows's bootloader instead? That will let med boot into Windows and Ubuntu.

---

### Post by oldfred on 2014-06-19
Dynamic partitions have their own issues. If you want to keep them you can. But Linux will not see any data inside them. And Windows cannot read any data inside Linux partitions.

You really want Windows boot loader on sda and grub on sdb. Do not use Boot-Repairs auto fix as that just installs grub to every MBR.
Boot-Repairs advanced mode usually lets you choose which system and which drive to install a boot loader. But with the dynamic partitions not sure if it will let you install Windows boot loader to sda. You can just use Linux to install lilo boot loader to sda.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

    
       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

---

