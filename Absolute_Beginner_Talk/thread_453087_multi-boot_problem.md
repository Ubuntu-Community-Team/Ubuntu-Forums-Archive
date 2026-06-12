---
title: "multi-boot problem"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by doom3d on 2007-05-24
Hi,

I had the following problem: My Win XP crashed due to an unkonwn blaster32 variant, and I have reinstalled it. During that grub-loader was deleted. So now I don!t have acces to my Ubuntu.
Tried to use Linux install CD +F6+ *rescue* option, but I still don!t have acces to my linux partitions. This *rescue* command was simply ignored.  What I am doing wrong?
I have important files there, reinstalling Linux would destroy them.
I am a beginner in Linux, started with Ubuntu in 2006 dec., so please, help!
[email]doom3d@atw.hu[/email]

Thanks.

Doom3d

P.S. I need that WinXP because I can!t manage to install my Lexmark 1180 printer  on Ubuntu..

---

### Post by igknighted on 2007-05-24
Fairly common issue.  You simply boot all the way to the liveCD desktop (its not windows, rescue mode isn't separate) and follow the direction in the Ubuntu WIKI.  It's typically a good idea to check the wiki first thing when you have a problem like this, as most of the answers are there :).  Here's the link you want: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub)

EDIT: You want to skip the "overwriting the windows bootloader" section.

---

### Post by alienexplorers on 2007-05-24
Use your LiveCD and boot it up.  
Enter > sudo grub
You will get an output like (hd0,0)
enter > root (hd#,#)
enter > setup (hd#)

---

### Post by doom3d on 2007-05-24
Hi,

Thanks for feedback.

sudo -i
grub
*Nothing appeared, but following wiki
find /boot/grub/stage1
* boot/stage1 doesn!t exist
* step skipped, continue with mounting, from "overwriting win bootloader" section
* having Linux w/o Win is better, then Win w/o Linux.  I will try to install that printer once        ** more..

mkdir mnt/root
...
mount -t ext3 /dev/hda7 /mnt/root

* found my linux on hda7
* here I guessed, that A=0, 1-9 internally 0-8, so hda7 means (hd0,6).
>grub
grub> root (hd0,6)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,6)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

* Now I will reboot, see You later. Thanks.
(Edited)
After rebooting, the Grub menu appeared, but failed to load Linux. I have checked it, and found Root (hd0,7) instead of 0,6 specified above.
Strange.  After editing options manually, Root (hd0,6) worked. After 3rd reboot, it still try to use hd0,7. 

I have checked /boot/grub/menu.lst and found Root (hd0,7) there. After sudo gedit to (hd0,6) and restart, now it works propely.
As a bonus (or penalty?),  Windows is also there.
Thanks!

Doom3d

---

