---
title: "Error 22 AND error 18"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by rcrusk on 2007-09-04
As a complete neophyte to this game, I have probably just made a simple error but need help now.
I installed as directed by the many forum articles on installation with a LIve CD.
Everything loaded fine to the partition I had hoped for.  But no go with the subsequent boot.  I then used SuperGrub to fix the problem and since then I have had the Error 22 on the first  selection for the dual boot and any other boot requests are an Error 18.

Some general info:
Dual SATA drives, no IDE
/dev/sdb1 XP
/dev/sdb6 Vista (seen in the boot option)
/dev/sdb9 Ubuntu (with a boot flag in the Gparted screen)
/dev/sdb10 linux-swap

find /boot/grub/stage1  = hd1,8 which I used to install the grub to the mbr.

Any suggestions for fixing this or do I reformat the lot and start again?

---

### Post by logos34 on 2007-09-05
have you seen this page?
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by rcrusk on 2007-09-05
I have seen that link.  Thats what got me to Supergrub.
More info on the problem:
Seems that the ntfs loader is missing and when I boot back into windows XP, the vista drive is viewed as corrupted.  I must have changed or deleted the loader.  I will try boot into vista and see what that does.

So the question is: can this be fixed from inside ubuntu (i did manage to get it booted by switching hte hard drives in supergrub) by modifying the grub?  Or do I have to reformat everything and just do a fresh install?  I would hate to loose all that data (not that it is life changing or anything).

Any help would be appreciated.  Thanx

---

### Post by logos34 on 2007-09-06
> **rcrusk said:**
> can this be fixed from inside ubuntu (i did manage to get it booted by switching hte hard drives in supergrub) by modifying the grub?  Or do I have to reformat everything and just do a fresh install?  I would hate to loose all that data (not that it is life changing or anything).

Open a terminal in ubuntu and type:

sudo fdisk -l (lowercase L)

cat /boot/grub/menu.lst /boot/grub/device.map

Post it.

What exactly did you do in Supergrub?  And what is the hard disk boot order in the Bios?

Not sure exactly what the issue is with XP and Vista, but you should have installed XP first, then Vista.  XP's NTLDR can't boot vista, you have to use vista boot manager to boot XP. When you install vista after XP it detects the latter as the 'active' partition and puts the boot files there.  And you should only have one entry in the grub menu for windows (vista)--you select vista then get a windows screen where you choose either vista or xp.   

One of these links might help you:
[http://www.microsoft.com/whdc/driver/tips/debug_vista.mspx](http://www.microsoft.com/whdc/driver/tips/debug_vista.mspx)
[http://support.microsoft.com/kb/927817](http://support.microsoft.com/kb/927817)
[http://support.microsoft.com/kb/927391](http://support.microsoft.com/kb/927391)
[http://msdn2.microsoft.com/en-us/library/aa468626.aspx](http://msdn2.microsoft.com/en-us/library/aa468626.aspx)

---

