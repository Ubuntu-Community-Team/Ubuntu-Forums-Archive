---
title: "Stage1 folder is gone, can I reinstall Grub???"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2008-02-25
I reinstalled from a partimage backup....and stage1 is gone...

Help???

---

### Post by Duck2006 on 2008-02-25
Yes this may help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by gohanssjn on 2008-02-25
I went there, but everything I see says it needs Stage 1 :confused:

---

### Post by Duck2006 on 2008-02-25
This is the grub manual you will find what you need to reinstall grub on here.

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by gohanssjn on 2008-02-25
sudo grub-install 'hd0'
Could not find device for /boot: Not found or not a block device.

:(

But I can see and browse the drive from the LiveCD!!!

---

### Post by gohanssjn on 2008-02-25
Oh, but now fd-sk cannot see it :(

---

### Post by Duck2006 on 2008-02-25
Try

grub-install /dev/hd0

As in part 3.3 for the grub manual.

---

### Post by Belak on 2008-02-25
My recommendation is to go into synaptic and reinstall grub.
After you reinstall the grub package, you can (hopefully) run the grub-install commands listed above.

Cheers,
Belak

---

### Post by gohanssjn on 2008-02-25
Well, I think what was the problem was an inappropiate entry in my partition table.  So I zeroed the drive,a dn am trying again to restore my backup.  At least now fdisk sees it.

---

### Post by gohanssjn on 2008-02-25
Nope, arter the restore by Partimage, the drive is missing again.  What is going on :(

Is there like a chkdisk alternative for Linux so I can check this thing?

---

### Post by gohanssjn on 2008-02-25
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       11325    90968031   83  Linux
/dev/sda2           11326       11978     5245222+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ grub-install 'hd0'
mkdir: cannot create directory `/boot/grub': Permission denied
ubuntu@ubuntu:~$ sudo grub-install 'hd0'
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$

---

### Post by gohanssjn on 2008-02-25
Wow, won't even work with SuperGrub.  maybe the image is messed up.  Which is a shame, because I need the computer tomorrow, and I'll just have to restore Vista onto it :(

EDIT:

WOAH.  Booting with supergrub.  Must be a way to fix it then :D

---

### Post by gohanssjn on 2008-02-26
Please :(

Someone has to know what to do.  I can browse the files, but when i tell grub to install, or 'root (hd0,0)' it tells me the disk does not exist :(

---

### Post by gohanssjn on 2008-02-26
Ok, followed the list here, and GRUB itslef gets further...
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
...however, then Loading Grub Stage1.5 just fills the screen over and over again.

---

