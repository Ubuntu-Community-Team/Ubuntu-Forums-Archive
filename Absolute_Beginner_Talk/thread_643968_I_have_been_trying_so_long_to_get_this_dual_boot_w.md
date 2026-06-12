---
title: "I have been trying so long to get this dual boot working.Please help"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Killamurk07 on 2007-12-18
Ok for so long I have been trying trying and trying..I have 2 Hard Drive both are in Master state. Everytime I try to boot Ubuntu It keeps selecting Windows XP. How can I get it to select Ubuntu? This is the process I did to install . 

First: I installed Ubuntu 7.04 (had it set to master)
Second: I did a fresh install OF WINDOWS XP (had it set to master)
While 1 system was installing I always had the second hard Drive unplug

Please tell me what I can do so I can select which one to boot. I can reinstall both windows.

---

### Post by spydon on 2007-12-18
Maybe a reinstallation of GRUB could solve this.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by arashiko28 on 2007-12-18
You must have both of the disks running, and when you choose where to install Ubuntu, you must see the Windows partition or in this case, the Disk with the partition and free space and the other disk. Then you choose where to install it. You must do this because Ubuntu modifies the MBR of windows and if you have it unplugged and then connect them both on master, the BIOS will conflict (I guess). I have done 4 dual boot installations, 3 with Gutsy and always has been at first shot.
By the way, I guess it will be better to set the jumpers on cable select. Any way, it doesn't matter.

---

### Post by Killamurk07 on 2007-12-18
Ok I will do that but do you recommend me removing the Windows XP HD? Oh yeah evertime the bios menu is up it says (PRIMARY IDE CHANNEL NO 80 CONDUCTOR CABLE INSTALLED)

---

### Post by Cypher on 2007-12-18
You can have the 2 HD's set at Master on seperate buses, but to be on the same bus you'd want to make one of them Slave.

The ideal installation steps is to install Windows XP first, on whichever HD giving it as much as space you'd think you'll need in there. Once you've confirmed that the WinXP is working properly, install Ubuntu and allow it to install GRUB on the boot drive. More often then not, the Ubuntu installation will find the WinXP installation and automatically add it as a menu option in the Grub menu.

When you now reboot, you should have the Grub menu and Ubuntu/WinXP options. If you don't have the WinXP option, boot into Ubuntu and we can tell you the file to modify to get the WinXP option in Grub.

---

### Post by A$h X on 2007-12-18
I agree that "cable select" for the drives is better than master on both. Regarding the dual boot, install windows first, then install ubuntu second (onto the same drive I guess). It should then edit the MBR and stick grub bootloader on it, so when you boot, you get a choice of which OS to use. 

I think you MIGHT be able to install windows and ubuntu onto different HD's, and then install grub manually on the primary HD using a live CD of some sort. But don't take my word on it, wait for a more experienced member's advice.

---

### Post by Killamurk07 on 2007-12-18
Thanks You  Guys So Much!! It Finally Works!! This Is What I Had To Do..


> *make Sure You Have Windows Xp Installed First On Second Hard Drive Make Sure Cable Pin Is In (slave Mode)
*then On The Other Hard Drive Install Ubuntu Make Sure The Hard Drive Pin Is Set To (master Mode) 
*then The Hard Drive That Have Windows Xp Is Still Connect While Installing Ubuntu..
*at 50-100% Of Finalizing Installation It Will Ask Do You Want To Install Grub On The Windows Xp Portion So It Will Detect It In The Ubuntu Dual Boot Options..
*thats It Your Done!!
Thanks Guys For Helping Me I Hope This Little Guide Help Others!

---

### Post by spydon on 2007-12-22
> **Killamurk07 said:**
> Thanks You  Guys So Much!! It Finally Works!! This Is What I Had To Do..

Now you can mark this thread as solved :). Thread tools>Mark thread as solved.

---

