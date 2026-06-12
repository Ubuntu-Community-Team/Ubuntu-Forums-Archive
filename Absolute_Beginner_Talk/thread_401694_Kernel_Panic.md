---
title: "Kernel Panic"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Joka999 on 2007-04-04
Right just re-installed Ubuntu, now i dual-boot Windows XP and Linux Ubuntu. Installed Ubuntu, restarted laptop then i updated Ubuntu, then while updating my laptop just turned off when i turned it back on and tried booting up Ubuntu it says :"kernel-panic not syncing: VFS: unable to mount root fs on unknown-block(0,0)". Please help as i just re-installed Ubuntu after other problems and i want to use Windows XP on virtualbox :D

---

### Post by Origin415 on 2007-04-04
What is the layout of the partitions on your hard drive?
I would think that if you had windows xp first, it would be on the first partition, but the linux kernel seems to be trying to boot that.

---

### Post by woooee on 2007-04-05
The boot menu should give you more than one boot option.  One for MSWindows and perhaps more than one for Ubuntu.  If you were upgrading the kernel when the machine went down, the boot manager is looking for a kernel that probably isn't in /boot so you should boot the old Ubuntu kernel option or MSWindows.  There is also a recovery mode option, but I'm not sure if that will help here.

---

### Post by Joka999 on 2007-04-05
I have the Grub boot menu and i can load up Windows, and how do i boot the old Kernel becuase i have 2 different kernels to choose from on my boot menu and i tried both and both had the same error. thanx for your reply

---

### Post by igknighted on 2007-04-05
> **Joka999 said:**
> I have the Grub boot menu and i can load up Windows, and how do i boot the old Kernel becuase i have 2 different kernels to choose from on my boot menu and i tried both and both had the same error. thanx for your reply

The problem isn't your kernels, its the grub entry.  Somehow grub is pointing to the wrong partition as the root partition, so when the kernel tries to mount it, it cannot.  Look in the wiki, I know theres a how to for messing with the grub menu at boot.  You could also boot the live CD and reinstall grub, that should fix it too if you don't want to mess around as much.  A quick forum search should turn up plenty of guides for that.  Just go through the motions like grub was lost doing a Windows install and you are trying to get it back.

---

### Post by Joka999 on 2007-04-05
Will this work??

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

Now the explanation.
Sudo grub gets you the grub shell.
Find /boot/grub/stage1 has grub locate the file stage1. What this does is tell us where grub's files are. Only a small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup. So you find the files and then you tell grub where to locate the files it will need for setup.
So root (hd?,?) tells grub it's files are on that partition.
Finally setup (hd0) tells grub to setup on hd0. When you give grub the parameter hd0 with no following value for a partition, grub will use the mbr. hd0 is the grub label for the first drive's mbr.
Quit will exit you from the grub shell.

---

### Post by Joka999 on 2007-04-06
Right i tried that, and i found all that does is put Grub on MBR which isn't my problem. SO any help??

---

### Post by accludetuner on 2007-04-08
I had a somewhat similar situation with a 4-OS boot that I resolved here:
[http://ubuntuforums.org/showthread.php?t=403890](http://ubuntuforums.org/showthread.php?t=403890)

---

