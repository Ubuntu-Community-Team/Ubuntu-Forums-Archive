---
title: "Need help dual booting 2 drives"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by onemind on 2006-12-07
Hi,

I have just installed ubuntu 6.06 LTS to my primary master drive. I have windows xp on a second slave drive. How do i set it up so i can choose at startup what os to load? Is it just a matter of adding a line some for grub?

Total noob here so please no technical linux speak :)

Thanks

---

### Post by louieb on 2006-12-08
Yes its just a matter of adding an entry to menu.lst.
I Dual boot Ubuntu on primary and XP on secondary drive.
Open Applications > Accessories > terminal[LIST]
[*]Backup ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```
[*]Edit ```
gksudo gedit /boot/grub/menu.lst
```
[*]Add following below line ### END DEBIAN AUTOMAGIC KERNELS LIST
```
title Win XP Home
                map (hd0) (hd1)
                map (hd1) (hd0)
                rootnoverify (hd1,0)
                makeactive
                chainloader +1
                boot

```[/LIST]That is how I did it. It should work for you too.

---

### Post by onemind on 2006-12-08
Sweet :)

Works! Thanks alot :)

---

### Post by Larry Roll on 2006-12-09
This did not work for me.  I keep getting the error message:  Cannot create regular file `/boot/grub/menu.lst_bak': Permission denied

What am I doing wrong?  

I am also trying to establish a dual-drive, dual-boot system with two drives, one with Windows XP Home loaded (and working when used as the only drive in the computer) and Ubuntu 6.06 loaded and working on another drive.  The Ubuntu drive is plugged into the original drive location with the original drive connection (Sata 0) and the Ubuntu drive is plugged into SATA 1.  The jumper is removed on the Windows drive.  There is no jumper on the Windows drive either.  I've learned last weekend that SATA doesn't need jumpers.  

Please explain each and every term you use.  I am not a computer professional -- I am a totally lost, confused, and helpless newbie.  Any technical terms at all will cause me to come to a full comprehension block -- so PLEASE EXPLAIN ANY TERM NO MATTER HOW SIMPLE AND EVERYDAY THEY SEEM TO YOU.  I am an ABSOLUTE BEGINNER and this is the ABSOLUTE BEGINNER forum.  Please keep that foremost in your mind. I'm here because I need help with the training wheels ON.

---

### Post by confused57 on 2006-12-09
> **Larry Roll said:**
> This did not work for me.  I keep getting the error message:  Cannot create regular file `/boot/grub/menu.lst_bak': Permission denied

What am I doing wrong?  

I am also trying to establish a dual-drive, dual-boot system with two drives, one with Windows XP Home loaded (and working when used as the only drive in the computer) and Ubuntu 6.06 loaded and working on another drive.  The Ubuntu drive is plugged into the original drive location with the original drive connection (Sata 0) and the Ubuntu drive is plugged into SATA 1.  The jumper is removed on the Windows drive.  There is no jumper on the Windows drive either.  I've learned last weekend that SATA doesn't need jumpers.  

Please explain each and every term you use.  I am not a computer professional -- I am a totally lost, confused, and helpless newbie.  Any technical terms at all will cause me to come to a full comprehension block -- so PLEASE EXPLAIN ANY TERM NO MATTER HOW SIMPLE AND EVERYDAY THEY SEEM TO YOU.  I am an ABSOLUTE BEGINNER and this is the ABSOLUTE BEGINNER forum.  Please keep that foremost in your mind. I'm here because I need help with the training wheels ON.

See this guide:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Believe you need to preface the cp command with sudo...

---

### Post by Larry Roll on 2006-12-09
OK, I checked out all those links.  They were beginning in the middle.  I need to begin at the beginning.  I need step-by-step directions which EXPLAIN ABSOLUTELY EVERYTHING on a word-for-word basis.  I will again outline my situation:

Computer:  Dell Dimension 8400, P-4 3 GHz, 1 GB RAM 

2 WD SATA drives, 1 is 250 GB and has Ubuntu 6.06 fully installed and working perfectly; 1 is a 160 GB and is the drive with the original Windows XP Home Edition installation and data files, including my iTunes and all my music, total of around 22 GB used on the disk.  

BOTH DRIVES ARE Serial ATA.  I have NO IDE drives.  Do not include any references to IDE drives in the instructions, that will only confuse me.  

The Ubuntu drive is the drive which boots.  The computer apparently doesn't know the Windows drive exists.  

I need to set this up with the Windows drive essentially untouched.  I can re-install Ubuntu on the 250 GB drive if necessary.  

I need the instructions to be SIMPLE and I need them to assume that I know absolutely NOTHING, because that is my reality.  I need to know how to type the commands in the terminal, with full explanations of how the terminal commands work, because I don't know that.  I have ZERO experience in using the terminal.  None.  Nada.  

This is the Absolute Beginner Forum.  I am an ABSOLUTE BEGINNER!  

I apologize for the high frustration level which is coming through in this post, but that's where I'm at.  Please Help!

---

### Post by riven0 on 2006-12-09
Larry, first things first.

Open the terminal. It should be in Applications >> Accessories >> Terminal

You'll get the terminal screen. 

Now copy and paste:

> sudo gedit /boot/grub/menu.lst

Hit enter and a text file should come up. At the very bottom, paste this:

> title Win XP Home
                map (hd0) (hd1)
                map (hd1) (hd0)
                rootnoverify (hd1,0)
                makeactive
                chainloader +1
                boot

Save the file. Now reboot the computer. Right before the Ubuntu splash screen appears, keep on hitting the esc key. You should get to a black screen with a lot of entries. One of them should say Win XP Home. Choose this one and you should boot up to windows.

---

### Post by Larry Roll on 2006-12-09
riven0:

Well, I did that.  Here's what happened -- I selected Win XP Home, and I got a memory test.  OK, I let the test go, and when it was over, I closed that window, and the computer booted up to Ubuntu.  

Any ideas as to why this happened?

---

### Post by riven0 on 2006-12-09
> **Larry Roll said:**
> riven0:

Well, I did that.  Here's what happened -- I selected Win XP Home, and I got a memory test.  OK, I let the test go, and when it was over, I closed that window, and the computer booted up to Ubuntu.  

Any ideas as to why this happened?

Alright, when you boot up to Ubuntu, go back to the terminal and type this:

> fdisk

Then paste the results here so I can see your setup.

---

### Post by confused57 on 2006-12-09
> **Larry Roll said:**
> riven0:

Well, I did that.  Here's what happened -- I selected Win XP Home, and I got a memory test.  OK, I let the test go, and when it was over, I closed that window, and the computer booted up to Ubuntu.  

Any ideas as to why this happened?
On my Dell, the first partition is a Dell Utility, Windows is actually on the 2nd partition...you'd need the entry rivenO gave you, but change the line with rootnoverify to (hd1,1).

Edit: You might want to post the output of:
```
fdisk -l
```
The -l is a small "L"

---

### Post by Larry Roll on 2006-12-09
> **riven0 said:**
> Alright, when you boot up to Ubuntu, go back to the terminal and type this:



Then paste the results here so I can see your setup.

OK riven0 here it is:

larry1@larry1-desktop:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
larry1@larry1-desktop:~$

---

### Post by riven0 on 2006-12-09
> **Larry Roll said:**
> OK riven0 here it is:

larry1@larry1-desktop:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
larry1@larry1-desktop:~$


Hmm, I think confused57 is right. I'm not seeing any ntfs system here. Can you try pasting the output of **fdisk -l** now?

---

### Post by Larry Roll on 2006-12-10
Success!  Confused's script change made it work.  I can now boot Windows from the GRUB menu.  Thanks, guys!  You helped a lot!  BTW, here's the output of fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           8       64228+  de  Dell Utility
/dev/sdb2   *           9       18994   152505045    7  HPFS/NTFS
/dev/sdb3           18996       19452     3670852+  db  CP/M / CTOS / ...
larry1@larry1-desktop:~$
larry1@larry1-desktop:~$

So -- what does all this mean?  

BTW2 -- I figured out that I have to precede "fdisk -1" with 'sudo' then give my password.  Is that true for all terminal commands?

---

### Post by riven0 on 2006-12-10
> **Larry Roll said:**
> Success!  Confused's script change made it work.  I can now boot Windows from the GRUB menu.  Thanks, guys!  You helped a lot!

Wonderful! :KS 

>  BTW, here's the output of fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           8       64228+  de  Dell Utility
/dev/sdb2   *           9       18994   152505045    7  HPFS/NTFS
/dev/sdb3           18996       19452     3670852+  db  CP/M / CTOS / ...
larry1@larry1-desktop:~$
larry1@larry1-desktop:~$

So -- what does all this mean?  

This shows detailed information on both your harddrives. The first one, (/dev/sda), is where linux is installed. I'm not good at explaining it, but it basically shows how the hd is partitioned, and what file system it is running under. Like the Extended should be the ext3 file system, and swap is like a backup for your memory. If anyone can explain it better I'd appreciate it.

The second one, (/dev/sdb) is what I was looking for. NTFS is where windows is installed. I wanted to make sure your grub was correctly pointing to it, but it looks like you figured it out yourself. :) 

> BTW2 -- I figured out that I have to precede "fdisk -1" with 'sudo' then give my password.  Is that true for all terminal commands?

It's only true for the commands that require superuser access, like installing programs or editing files that aren't in your /home folder. It's all for the sake of security and is one of the main reasons why you don't need an anti-virus app.

Enjoy Ubuntu :mrgreen:

---

