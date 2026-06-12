---
title: "dual boot with Ubuntu / XP on separate HD"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by crisco_chris on 2007-03-22
I am new to Ubuntu and linux so I need my had held a bit.

XP Pro is installed on my main HD and Ubuntu Edgy on an external drive.

I am unable to choose Ubuntu if the main HD is connected. 
When the external drive is the only drive connected ubuntu boots up without any problems

How can I edit my boot.ini to get the choice of which OS I want to use.


[INDENT]C:\bootpart>bootpart
Boot Partition 2.60 for WinNT/2K/XP (c)1995-2005 G. Vollant (info@winimage.com)
WEB : [http://www.winimage.com](http://www.winimage.com) and [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
Add partition in the Windows NT/2000/XP Multi-boot loader
Run "bootpart /?" for more information

Physical number of disk 0 : 13651365
 0 : C:* type=7  (HPFS/NTFS), size= 62910508 KB, Lba Pos=63
Physical number of disk 2 : 495df425
 1 : E:* type=83  (Linux native), size= 104391 KB, Lba Pos=63
 2 : E:  type=5  (Extended), size= 303885540 KB, Lba Pos=24900750
 3 : E:  type=7   (HPFS/NTFS), size= 62910500 KB, Lba Pos=24900829
 4 : E:  type=5   (Extended), size= 123371167 KB, Lba Pos=385929495
 5 : E:  type=7    (HPFS/NTFS), size= 123371135 KB, Lba Pos=385929559
 6 : E:  type=83  (Linux native), size= 10241437 KB, Lba Pos=208845
 7 : E:  type=82  (Linux swap), size= 2104515 KB, Lba Pos=20691720

C:\bootpart>bootpart list
Boot Partition 2.60 for WinNT/2K/XP (c)1995-2005 G. Vollant (info@winimage.com)
WEB : [http://www.winimage.com](http://www.winimage.com) and [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
Add partition in the Windows NT/2000/XP Multi-boot loader
List entry in BOOT.INI
 0 : multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professio
nal" /noexecute=optin /fastdetect /usepmtimer
 1 : C:\bootpart\bootsect.lnx="Unbuntu Linix"

By runnning "bootpart REMOVE <number>"
where number is an entry number, you can remove the entry from C:\BOOT.INI
[/INDENT]

---

### Post by mahy on 2007-03-22
It basically means your main HDD has higher boot priority in BIOS. You have to set it up in there.

---

### Post by mahy on 2007-03-22
Or, alternately, plug both your drives in, boot an ubuntu live cd and run the command

sudo grub-install [your main hdd name]

EDIT: There are some people who use the winxp bootloader (ntldr) to boot Ubuntu, but i personally think it's sick. You should use GRUB instead.

---

