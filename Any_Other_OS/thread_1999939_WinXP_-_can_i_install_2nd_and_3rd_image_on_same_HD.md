---
title: "WinXP - can i install 2nd and 3rd image on same HDD?"
date: 2012-06-08
forum: Any Other OS
---

### Post by bzd454 on 2012-06-08
Hi,
    i have a netbook with both WinXP and Ubuntu, and Grub is handling the boot process. I wanted to re-install WinXP from an early image that i took a few years ago because my current WinXP is getting slowed down by junk and then i started to wonder if i could just install that earlier image on a different partition and then maybe delete my current WinXP image later if necessary. This is a legal OEM version and it would stay on the same netbook but i'm not sure Windows allows multiple copies on the same computer and also, how can i get GRUB to work?

tia.

---

### Post by wilee-nilee on 2012-06-08
Multiple copies I don't believe so.

Is this a OEM from the same computer?

You might call MS and ask to get the real answer.

---

### Post by bzd454 on 2012-06-08
> **wilee-nilee said:**
> Multiple copies I don't believe so.

Is this a OEM from the same computer?

You might call MS and ask to get the real answer.



yes, its the same OS, i just made an earlier image of it.

---

### Post by LostFarmer on 2012-06-08
Is it possible-- yes.  Legal , do not know.

Grub will have no problem, the problem will be XP.  When XP boots it checks the registry to see where the OS partition start sector is at.  If it is not where is should be, XP will look at all fat32 and NTFS partitions and make a guess, some times wrong if more then on partition.  In your case it will likely use the slow XP partition and it will partial boot into both partitions and create a mess.

You would have 2 basic options to get it to work.
after putting the image into a new partition and updating grub: (will let some one else tell you how)

1) temporarily delete the slow XP partition (linux fdisk)
1b) boot into the new XP cloned copy, a couple times (so it will correct its registry)
1c: use testdisk (XP or linux version) and recover temporarily deleted XP partition.   (i think there is a cdisk command, before and after deleting partition that will work or back up the MBR before deleting and restore at this point)

2) boot into the old XP , use regedit  and correctly change registry of the new clone.  If I remember the reg key is 'HKLM, software,Mounted Devices'. 
  If this is the way you want to go , I will have to boot into XP to give better info.  (do not know when I will be back)

Both methods has its own risks.
I have 4 cloned copies on 2 different hdd's in my comp.

---

### Post by TheGuyWithTheFace on 2012-06-08
Wait, if you have a system image, what's stopping you from using windows backup? Or, does windows XP have a backup and restore center?

---

### Post by bzd454 on 2012-06-09
> **TheGuyWithTheFace said:**
> Wait, if you have a system image, what's stopping you from using windows backup? Or, does windows XP have a backup and restore center?

it had a Samsung Restore program with the hidden partition but i deleted it. 

@ LostFarmer - thanks for that post.  am trying to decide if i should try your method there as i'm kind of a noob in linux.

---

