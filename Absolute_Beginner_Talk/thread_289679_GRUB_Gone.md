---
title: "GRUB Gone"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by infin?ty on 2006-10-31
Hi all.
I just ran into a little problem, yesterday i formatted my C drive, i had a dual boot of ubuntu 6.06 and Windows Xp Pro. I formatted C drive and reinstalled win dows XP  but now the problem is that GRUB is gone(I shud've thought of this before).
Is there any way to rrestore grub without reinstaling ubuntu. I really had my ubuntu in a very good condition and now i dont want to reinstall it.

---

### Post by Bachstelze on 2006-10-31
If you had searched the Wiki, you'd have found [this](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)...

---

### Post by joshgtv6 on 2006-11-01
using the wiki directions for reinstalling grub from the Live CD gives me errors.  

Typing grub gets me the grub prompt.  The next step tells you to type:
find /boot/grub/stage1    That returns:
Error 15: File not found

So now what?  the wiki says nothing about what to do when it returns an error.  it just assumes that everything will work sweet as pie. So where do I go from here.  I'm dual booting XP and 6.06 on two hardrives and i'm keeping them completely seperate from each other.  So i don't want GRUB to overwrite the MBR for XP.  6.06 is on my slave drive.  

Here is my fdisk info if it helps.  I've been looking at the wiki and other sources and there seems to be 100 different ways to restore GRUB.  If someone could help me do this so I don't overwrite the MBR of XP i would appreciate it. 

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4862    39053983+   7  HPFS/NTFS

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       35345   283908681   83  Linux
/dev/hdb2           35346       36481     9124920    5  Extended
/dev/hdb5           35346       36481     9124888+  82  Linux swap / Solaris
ubuntu@ubuntu:~$


Edit: i'm using the Live CD for Ubuntu to do all this

---

### Post by Herman on 2006-11-02
>  Typing grub gets me the grub prompt.  The next step tells you to type:
find /boot/grub/stage1    That returns:
Error 15: File not found Hello joshgtv6,
You need to type 'sudo grub' for a grub shell with root priveleges. An ordinary Grub shell isn't very powerful.
```
sudo grub
``` That's probably all you're doing wrong.
Here is my own version of how to                               Re-install Grub with a GRUB shell eg; with Live CD..........................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")
Regards, Herman :D

---

