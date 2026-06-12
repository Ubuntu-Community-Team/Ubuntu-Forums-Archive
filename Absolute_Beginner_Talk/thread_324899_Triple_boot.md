---
title: "Triple boot?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by eranical on 2006-12-24
Hi,
I wish I had previously come across this forum. I tried to install Red hat a few months back & ended up having to use fdisk to repartition & then format my harddrive.](*,) ](*,) 
My situation is thus: I need for work related purposes Win XP & 2000 once in a while, so have it set up with dual boot. Now my problem is I would like to install Ubuntu too. Would it be possible to have all 3 OS's. If not as a last resort I could install Win 2000 on a seperate hdd & swap drives when the rare need of 2000 arises. but then my question is how do I uninstall it from the present hard disk. 
My current partitions are 25gb for xp, 25 gb for 2k & 185gb as a data area... I also just noticed that the data partition is in NTFS so I guess I won't have acces to it from ubuntu unless I chg it to fat 32 if that is possible... Any help greatly appreciated..

---

### Post by Frak on 2006-12-24
1. I see no reason why you won't be able to install Ubuntu on the extra area, the GRUB bootloader should easily recognize both partitions, and map it to boot

2a. If you want to uninstall 2000, as I remember, put in the startup disc, exit out of the startup menu, and type uninstall.exe, and it will uninstall 2000, but I've heard of problems with it also uninstalling XP.

2b. An easier way to uninstall 2000 would be to use GParted and wipe that partition off of the HDD.

2c. If you installed 2000 onto a different HDD, you would have to install GRUB or Super GRUB onto the other drive, because windows won't install if its not on the C:\ drive, so you have to install GRUB or Super GRUB to make windows think it is.

3. Ubuntu could easily change that NTFS partition into an Ext3 Partition and add its own Swap, thats all done, during installation, without human interaction, it will do it automatically.

That should do it, Merry Christmas!

---

### Post by diatribe on 2006-12-24
When you install ubuntu, just dont install grub on the master boot record ( you need the laternate install iso for this I elieve) then just add a new entry into your current menu.lst pointing to the new image.

---

### Post by eranical on 2006-12-24
> **Frak said:**
> 1. I see no reason why you won't be able to install Ubuntu on the extra area, the GRUB bootloader should easily recognize both partitions, and map it to boot

2a. If you want to uninstall 2000, as I remember, put in the startup disc, exit out of the startup menu, and type uninstall.exe, and it will uninstall 2000, but I've heard of problems with it also uninstalling XP.
[SIZE="2"][SIZE="3"]I have also heard of the similar problems. The cancer is tough to get rid of eh?[/SIZE][/SIZE]

2b. An easier way to uninstall 2000 would be to use GParted and wipe that partition off of the HDD.

2c. If you installed 2000 onto a different HDD, you would have to install GRUB or Super GRUB onto the other drive, because windows won't install if its not on the C:\ drive, so you have to install GRUB or Super GRUB to make windows think it is.
[SIZE="3"]Here what i was thinking was off leaving the cabinet open and physicaly changing the hdd, like disconecting the main drive. It will not allow me to share many files though that is not really important since the stuff I may need to use on both 2k & Xp is mainly online..[/SIZE]

3. Ubuntu could easily change that NTFS partition into an Ext3 Partition and add its own Swap, thats all done, during installation, without human interaction, it will do it automatically.

That should do it, Merry Christmas!

[SIZE="3"]Thanks and the same to you as well...[/SIZE]

---

### Post by Sef on 2006-12-24
1) Before dual or triple booting or more, **back up** your data.  Usually there is no problem but at times, the install does not go well.

2) Use the Live CD first and see how your computer runs on it.  If there are problems when using the Live CD then likely that same problem will exist upon install.

---

### Post by eranical on 2006-12-24
> **Sef said:**
> 1) Before dual or triple booting or more, **back up** your data.  Usually there is no problem but at times, the install does not go well.

2) Use the Live CD first and see how your computer runs on it.  If there are problems when using the Live CD then likely that same problem will exist upon install.

My previous experience with red hat taught me the importance of backing up!
I did use the live cd a few times & really liked the feel and interface though I only used the GUI. Haven't used a comand prompt in a long time. However after reading the posts here I feel confident I can do it

---

