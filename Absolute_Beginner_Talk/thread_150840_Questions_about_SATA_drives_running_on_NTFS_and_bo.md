---
title: "Questions about SATA drives running on NTFS and bootups"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by Nunyah on 2006-03-26
Hey all
A couple of newbish questions.. ;)
**#1**
I'm trying to locate two Western Digital 320GB SATA disks. They are using NTFS filesystem and will continue to, but I only need to read from the disks so it's not a problem.. Is there something like 'manage' in Ubuntu?
My system disk is cut up on half, one for linux, the other for Windows XP, I'm guessing the disk that's named hdb1 is the other half where XP is installed. I cannot read the drive, is it XP that's securing the filsystem since it contain system information? Can I bypass it somehow?
[B]
#2[/B]
If I where to erase the part with XP installed and say reinstall it with either XP or 2000, would it make it a bit complicated with the Linux boot loader? I know it's not a problem the other way around... and I do **not** wanna leave ubuntu behind but I wanna play Oblivion! :p

---

### Post by Sutekh on 2006-03-26
[QUOTE=Nunyah]
**#1**
I'm trying to locate two Western Digital 320GB SATA disks. They are using NTFS filesystem and will continue to, but I only need to read from the disks so it's not a problem.. Is there something like 'manage' in Ubuntu?
[/QUOTE]
 - Can you post the output of these two commands?

**Edit: **- I thought this might be a bit ambiguous.  You need to open a Terminal Window (from the Applications -> Accessories menu) and enter these commands.  When prompted for a pasword you need to use your user's password.
**End Edit**


```
sudo fdisk -l
```
 - This will list all the partitions on your hard discs
```
cat /etc/fstab
```
- This will show how these partitions are mounted in Ubuntu (if at all), then we can show you how to mount them correctly.  Since they are NTFS you won't be able to write to them, but you already know that.


[quote=Nunyah]My system disk is cut up on half, one for linux, the other for Windows XP, I'm guessing the disk that's named hdb1 is the other half where XP is installed. I cannot read the drive, is it XP that's securing the filsystem since it contain system information? Can I bypass it somehow?
[/QUOTE]
 - It is possible that Windows XP has secured those files, I'm going to try and find out where you can turn this off.

[http://www.ubuntuforums.org/showthread.php?t=140809](http://www.ubuntuforums.org/showthread.php?t=140809)


[quote=Nunyah]
**#2**
If I where to erase the part with XP installed and say reinstall it with either XP or 2000, would it make it a bit complicated with the Linux boot loader? I know it's not a problem the other way around... and I do **not** wanna leave ubuntu behind but I wanna play Oblivion! :p[/QUOTE]
 - When you install Windows again, it will write over the MBR of the disc that it is installed on.  If GRUB was there previously it will be overwritten.

 - You can get GRUB back on the MBR using this information

[Ubuntu Wiki - Recovering Ubuntu After Installing Windows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Nunyah on 2006-03-26
Did a screendump. I see them both with fdisk -1, not with cat fstab, meaning I'll have to mount them in order to make them visible?

---

### Post by Sutekh on 2006-03-26
[QUOTE=Nunyah]Did a screendump. I see them both with fdisk -1, not with cat fstab, meaning I'll have to mount them in order to make them visible?[/QUOTE]

Yep they are not in the /etc/fstab so we'll add them in manually

First create some folders to mount them to
```
sudo mkdir /media/drive1 /media/drive2
```
(You don't have to use drive1, drive2 if you don't want to)

Then use this code to backup and edit the fstab
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```

Then add these lines to access the 320GB drives
```
/dev/sda1   /media/drive1   ntfs   nls=utf8,umask=0222   0   0
/dev/sdb1   /media/drive2   ntfs   nls=utf8,umask=0222   0   0
```

Save the file (Ctrl+O) and exit (Ctrl+X)

Finally issue this command to remount the partitions without rebooting
```
sudo mount-a
```

You should be able to see these drives on your desktop and be able to read and execute files on them, but not write to them.

---

### Post by Nunyah on 2006-03-26
Thanks man, really appreciate your help in this, both disks are up and running!
Also thanks for the links, now I do not have to worry about Windows hijacking the bootloader if I reinstall it. :)

About the NTFS systemdisk being locked, it's not a problem. Was asking more of curiousity than needing to access it.

---

### Post by Sutekh on 2006-03-26
Hey glad its working

You can access the Windows partition - hdb1 - if you want

Open up the /etc/fstab and change this line
```
/dev/hdb1    /media/hdb1    ntfs    defaults    0    0
```
to this one
```
/dev/hdb1    /media/hdb1    ntfs    nls=utf8,umask=0222    0    0
```Just like for the 320GB discs (thats a lot o memory :))

---

### Post by Nunyah on 2006-03-26
Hmm, opens up but showing nothing. I did the sudo mount -a command to update it afterwards..

**Update:**Got it working after a reboot. Thanks :)

---

