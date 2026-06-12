---
title: "Fouled up Installation"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by linux phreak on 2008-02-18
Hi.I downloaded and Installed Pclinux OS today.The install was not as straight forward as Ubuntu's and in the end i got the 'error loading os' message when i rebooted the system and i had Xp installed previously.The computer is refusing to load either operating systems.In gparted i see that Xp is indeed there.Please guide me.

---

### Post by bumanie on 2008-02-18
Please post the output of terminal command
sudo fdisk -l

---

### Post by sabatron on 2008-02-18
What does your gparted look like?  As in how did you partition your drive.  And how much did you leave for swap?

---

### Post by linux phreak on 2008-02-18
Output of fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
16 heads, 63 sectors/track, 79656 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xc43ec43e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       55272    27856678+   7  HPFS/NTFS
/dev/sda2           55273       79656    12289536    5  Extended
/dev/sda5           55273       77620    11263360+  83  Linux
/dev/sda6           77621       79656     1026112+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa03fdce7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6119    49150836    7  HPFS/NTFS
/dev/sdb2            6120       19456   107129452+   f  W95 Ext'd (LBA)
/dev/sdb5            6120       12238    49150836    7  HPFS/NTFS
/dev/sdb6           12239       19456    57978553+   7  HPFS/NTFS

---

### Post by linux phreak on 2008-02-18
I was tired of waiting for hardy heron so i decided to try the famous PclinuxOs and God i regret it.I ended up damaging my boot up and also managed to destroy my Gutsy.

---

### Post by bumanie on 2008-02-18
What do you want to do? Do you want to be able to boot into windows only, try and reinstall grub of pclinux or reinstall gutsy and in theory (as long as everything goes well), a reisntalled gutsy should fix the grub bootloader and again giv eyou a choice of windows or gutsy to boot to.
Also do you have a windows disk?

---

### Post by linux phreak on 2008-02-18
Thank you for you reply.I want Xp and pclinux os(now that i have installed it).as dual boot.Also i do have my Xp disk

---

### Post by bumanie on 2008-02-18
Does your pclinux use grub or lilo as the bootloader? I assume grub, but have seen some references to lilo being used by pclinux.

---

### Post by linux phreak on 2008-02-18
I am terribly sorry friend i do not know that.I remember seeing VMLINUZ or something like that during bootup i hope that it is a sign of GRUB

---

### Post by bumanie on 2008-02-18
Vmlinuz is the kernel. May be you should look and see if there is a pclinux help forum, anything I say is a stab in the dark as I have never used or even seen pclinux in action. What are you accessing the internet with now? If it is the pclinux live cd, you should be able to reinstall grub from it.

---

### Post by linux phreak on 2008-02-18
I am doing this from my gutsy Live CD.If it is grub, how can we Reinstall it.I can write it down and do it when i boot from the pclos CD

---

### Post by jonny5tails on 2008-02-18
If you've got room on your hard drive, go ahead & install Hardy (I've got Hardy - Ubuntu & Kubuntu installed presently, along with Vista & Gutsy). Hardy (Alpha 4) seems to be stable, & if you install it, you can install the boot loader to regain all of your other installations (although you might have to edit menu.lst).\\:D/

---

### Post by bumanie on 2008-02-18
Follow this guide [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
As far as I know it won't matter whether you do it from a live gutsy cd or a live pclinux cd, because neither are on the harddrive, they are just directing grub to boot from a certain partition.
I hope this helps, if not you should visist here [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
and do a lot of reading. You could also download super grub disc and try it - it often can fix grub problems. Get it from here [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)
Good luck.

---

### Post by linux phreak on 2008-02-18
Hi Jonny, the situation is that i have installed pclos and as i am an idiot i managed to foul up the Grub.I have both xp and pclos installed but i cannot access either of them because of the GRUB.

---

