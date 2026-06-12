---
title: "Booting Win2k from grub"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2006-02-10
HDD arrangment:

1 80GB IDE HDD mounted as /dev/hdb
1 160GB SATA HDD mounted as /dev/sda
1 300GB SATA HDD mounted as /dev/sdb

I have windows 2000 installed on the 160GB drive, but since it was not the computer's primary drive when I installed windows, none of the startup files got installed it it (boot.ini etc)

I want to be able to boot to this install with grub, but I can't. I don't want to have to reinstall windows because it is a hassle due to driver issues and everything in that install is as I like it. What files do I need on the root of the drive, and what config code do I need in my menu.lst to boot?

---

### Post by BenTyreman on 2006-02-10
[http://support.microsoft.com/?kbid=318728](http://support.microsoft.com/?kbid=318728) should sort you out, if you have the original setup CD-ROM. In particular
```

Method 2: Use the Recovery Console
1.	Use the Windows 2000 Setup disks to restart the computer, or use the Windows 2000 CD-ROM to restart the computer.
2.	At the Welcome to Setup screen, press R to repair the Windows 2000 installation.
3.	Press C to repair the Windows 2000 installation by using the Recovery Console.
4.	Type the number that corresponds to the Windows installation that you want to repair, and then press ENTER. For example, type 1, and then press ENTER. For additional information, click the article number below to view the article in the Microsoft Knowledge Base:
229716 (http://support.microsoft.com/kb/229716/EN-US/) Description of the Windows Recovery Console
5.	Type the Administrator password, and then press ENTER.
6.	Type map, and then press ENTER. Note the drive letter that is assigned to the CD-ROM drive that contains the Windows 2000 CD-ROM.
7.	Type the following commands, pressing ENTER after you type each one, where drive is the drive letter that you typed in step 4 of "Method 2: Use the Recovery Console," of this article:
copy drive:\i386\ntldr c:\

copy drive:\i386\ntdetect.com c:\
If you are prompted to overwrite the file, type y, and then press ENTER.

NOTE: In these commands, there is a space between the ntldr and c:\, and between ntdetect.com and c:\.
8.	Type the following command, and then press ENTER:
type c:\Boot.ini
A list similar to the following list appears:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect
						

If you receive the following message, the Boot.ini file may be missing or damaged:
The system cannot find the file or directory specified.
9.	If the Boot.ini file is missing or damaged, create a new one. To do so, follow these steps:
a. 	Use a text editor, such as Notepad or Edit.com, to create a boot loader file similar to the following boot loader file:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect
						

For additional information, click the article number below to view the article in the Microsoft Knowledge Base:
102873 (http://support.microsoft.com/kb/102873/EN-US/) BOOT.INI and ARC Path Naming Conventions and Usage
301680 (http://support.microsoft.com/kb/301680/EN-US/) How To Create a Boot Disk for an NTFS or FAT Partition in Windows
b. 	Save the file to a floppy disk as Boot.ini.

NOTE: If you used Notepad to create the file, make sure that the .txt extension is not appended to the Boot.ini file name.
c. 	Type the following command at the Recovery Console command prompt to copy the Boot.ini file from the floppy disk to the computer:
copy a:\Boot.ini c:\
10.	Type exit, and then press ENTER. The computer restarts.

```

---

### Post by wr0x2 on 2006-02-10
Ok, thanks for the help, I'll probably try this tomorrow. Out of convenience, is there any reliable utility I can use to write them to the drive from linux? (Drive is NTFS formatted)

---

