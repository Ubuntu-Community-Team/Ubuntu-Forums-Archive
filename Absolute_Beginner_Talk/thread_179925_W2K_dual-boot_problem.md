---
title: "W2K dual-boot problem"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Chris@ on 2006-05-21
After installing 5.10 alongside W2K I am unable to access my W2K installation. 

Starting point was two W2K installations on separate NTFS partitions selectable via GRUB on a 160GB, ATA100 HDD.  

I followed the instructions on a 5.10 install disc, chose to delete the smaller partition (~76GB) to make free space for Ubuntu and completed the installation. 

The system now boots into GRUB, offers me 4 Ububtu options or W2K, but on selecting the W2K alternative I'm still offered the choice of two W2K installations (one of which is now deleted).  When I select the surviving W2K alternative, windows starts but up bluescreens with the message 
"STOP:0x0000007B........INACCESSIBLE_BOOT_DEVICE"

I have checked the GRUB code to ensure that it does contain the code for a windows option as suggested on another thread on this forum.

I want to learn how to do without the evil empire, but for now I still need Windows, so the question is, can I recover access to  the W2K installation and if so how?  Help?

---

### Post by it.henrik on 2006-05-21
You can try to reinstall the master boot record for win2k and then reinstall grub :)

from 
[http://support.microsoft.com/kb/q229716/](http://support.microsoft.com/kb/q229716/)

Starting the Windows Recovery Console
To start the Windows Recovery Console, use any of the following methods:
&#8226;	Start your computer with the Windows Setup floppy disks, or with the Windows CD-ROM. At the "Welcome to Setup" screen, press F10, or press R to repair, and then press C (Windows 2000 only) to start the Windows Recovery Console. Select the appropriate number for the Windows installation that you want to repair, and then type the administrator password. If the administrator password does not exist, just press ENTER.
&#8226;	Add the Windows Recovery Console to the Windows Startup folder by using Winnt32.exe with the /cmdcons switch. This procedure requires approximately 7 MB of hard disk space on your system partition to hold the Cmdcons folder and files. 

FIXBOOT
fixboot drive name:
Use this command (where drive name is the drive letter where the boot sector will be written) to write the new Windows boot sector code on the boot partition. This command fixes problems where the Windows boot sector is corrupted. The Emergency Repair process also fixes the boot sector. This command overrides the default of writing to the system boot partition.


FIXMBR
fixmbr device name
Use this command (where device name is an optional device name that specifies the device that needs a new MBR) to repair the master boot record (MBR) of the system partition. This command is used in scenarios where a virus has damaged the MBR and Windows cannot start.

WARNING: This command has the potential to damage your partition tables if a virus is present or a hardware problem exists. This command may lead to inaccessible partitions. Microsoft suggests running antivirus software before using this command.

The name can be obtained from the output of the map command. If this is left blank, the boot device's MBR is fixed, for example:
fixmbr \device\harddisk2
If Fixmbr detects an invalid or non-standard partition table signature, it prompts you for permission before rewriting the MBR.
FORMAT

---

### Post by Chris@ on 2006-05-21
Ran FIXBOOT.  It indicated a corrupted boot sector and claimed to have corrected it.

Now I have no W2K and no Linux!  Boot fails with message "NTLDR is missing"

OK, but when I start a 5.10 install as a route to installing GRUB, my HDD is now shown as a single 164GB FAT16 partition!

I hesitate to proceed further in case I do more damage.

---

### Post by confused57 on 2006-05-21
You could try booting up with the windows install CD, going to recovery mode and typing in fixmbr...this will hopefully allow you to boot into windows.

Then you'll need to restore grub to the windows mbr to be able to boot up Ubuntu.

I don't understand about the Ubuntu install CD showing one large partition, unless somehow your entire HD was  formatted.

Try to get windows up and running, then worry about restoring Grub.

---

### Post by Chris@ on 2006-05-22
Tried 'fixmbr'.

W2K boot now fails with message 'invalid partition table'.

I've since been reminded that a '164GB FAT16' partition is a crazy result as FAT16 doesn't recognise drivespace above about 6GB.

---

