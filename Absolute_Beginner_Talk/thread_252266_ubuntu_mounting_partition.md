---
title: "ubuntu mounting partition"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Bigguy2468 on 2006-09-06
Here is the question:
If you choose to manually mount ubuntu on the /root partition will the installation process still give you the option of where to install GRUB like on the MBR (Master Boot Record)?

My worry is that if I do the manual installation incorrectly that I will break the box and not be able to boot XP off the NTFS partition which is my work partition at the moment. 

I have googled and try to find any details explanation on how to install ubuntu on a system that already has a Linux distro and you want to overwrite the existing partitions. I have about 30gig allocated for Linux already for that partition and I don't want to waste that much memory for an OS that I probably won't use.

Any help on this would be appreciated.
:D

---

### Post by steve.horsley on 2006-09-06
Firstly, my understanding is that /root is the home directory for user root, and is not normally mounted on a separate partition. The root partition is the one mounted at /. 

Secondly, I believe only the "alternate" installer gives you an option as to where to install GRUB. I don't think using custom partitioning affects that option, but I don't remember for definite.

Bear in mind that you have the option of just deleting the old partitions and letting the installer use the unallocated space.

Whatever you do, grub should offer you the choice of XP, assuming you didn't delete it by mistake. In fact, I installed grub into the superblock of my Ubuntu partition (I use a different bootloader in the MBR), and grub **still** offers me a choice of Ubuntu or windows.

---

### Post by Bigguy2468 on 2006-09-06
> **steve.horsley said:**
> Firstly, my understanding is that /root is the home directory for user root, and is not normally mounted on a separate partition. The root partition is the one mounted at /. 

Secondly, I believe only the "alternate" installer gives you an option as to where to install GRUB. I don't think using custom partitioning affects that option, but I don't remember for definite.

Bear in mind that you have the option of just deleting the old partitions and letting the installer use the unallocated space.

Whatever you do, grub should offer you the choice of XP, assuming you didn't delete it by mistake. In fact, I installed grub into the superblock of my Ubuntu partition (I use a different bootloader in the MBR), and grub **still** offers me a choice of Ubuntu or windows.


Thank you for your reply.
Currently my system is using LILO as the Boot Loader. I take it that if I delete the Linux partitions that should not affect LILO correct? I mean if LILO is in the MBR I would think the result would be that the current choices I have there now would be showing, but if I were to try to boot into Mandriva it wouldn't work, correct?

My second question would be this:
IF I delete the Linux partitions, can I then click back and choose for ubuntu to use free space thereby allocating all the space other than is used for XP on the NTFS partition for ubuntu?

Thanks

---

### Post by xpod on 2006-09-06
It`s easy to fix the mbr if you do mess up.A bootdisk with "fdisk/mbr"...
As i just learned recently.........:-\"

---

### Post by gn2 on 2006-09-06
Be careful with any valuable data Xpod, fdisk fix mbr won't always work.....
I know, it happened to me. Nasty.

Is that Xpod as in Fox Xpod the carp/pike angling rod pod?

---

### Post by xpod on 2006-09-07
NO....XP had O.D`d

PS...dont keep valuable data on these things.....i like breaking them toooo much.....

EDIT:...Nothing "always" works...THATS how we learn what "sometimes" works:D

EDIT:....people with"valuable" stuff on pc`s should`nt be messing around with new operating systems UNLESS they are 100% sure they can afford to lose it OR
are sure they know what their doing......(especially the sudo i.t experts)

---

