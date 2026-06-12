---
title: "Hard drive not reading"
date: 2012-09-12
forum: Any Other OS
---

### Post by bert6253 on 2012-09-12
I was working with XP Pro os and it chrashed. Moved to ubuntu 11.04 and moved the XP Pro hard drive to the ubuntu system. HD worked just fine. This HD was a boot drive for XP Pro.
 
Purchased Win 7 system moved the XP Pro hard drive to the Win 7 however, win 7 does not reconized the format on the hard drive and wants to reformat. Currently there is data I would like to keep on the hard drive.
 
I moved the HD back to the ubuntu system and I am unable to see the data on the drive. I remember when I first hooked the HD to the ubuntu system it gave me a message about the formate type of the HD and wanted to make some change. I agreed to the change. 
 
I am new to this type of problem.

---

### Post by oldfred on 2012-09-12
Moved to other OS as it really is support question on Windows.

The first thing to try is chkdsk from a Windows repairCD or USB.

But I have used Windows 7 chkdsk on an XP install. It did work, maybe even better as it found more issues, but it installed a Windows 7 partition boot sector (PBR). I then had to use Windows 7 repairUSB to restore the PBR to XP type.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

