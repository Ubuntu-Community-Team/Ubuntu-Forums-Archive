---
title: "Help needed repairing Grub"
date: 2012-08-27
forum: Any Other OS
---

### Post by esc1 on 2012-08-27
Cloned a drive for backup, but GRUB is messed up after cloning. The cloned disc Posts, says GRUB, and doesn't go any farther. Decided Grub must be damaged from cloning. I was following the link [here]("http://ubuntuforums.org/showthread.php?t=224351") for the second chroot section since 'find /boot/grub/stage1' returns no results, but got hung up on 'sudo grub' part. It said sudo not found. Guessing I either didn't pick the right dev to mount (I picked sda6) or this is some kind of special circumstance.  

Pasting my fdisk in case someone needs to see it.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      562274      281106   83  Linux
/dev/sda2          562275   218853494   109145610   83  Linux
/dev/sda3       218853495   224411984     2779245   82  Linux swap / Solaris
/dev/sda4       224411985   312576704    44082360    5  Extended
/dev/sda5       224412048   304238969    39913461   83  Linux
/dev/sda6       304239033   307018214     1389591   83  Linux
/dev/sda7       307018278   312576704     2779213+  83  Linux

Thanks for any help!

---

### Post by oldfred on 2012-08-27
Do you have both clone and original drive mounted. Clone will have same UUIDs and system gets confused on which to use.

grub stage1 is from grub legacy which has not been the standard in Ubuntu since 9.04.

Most find this the easiest way to repair an install. And if not you can run the BootInfo report and post the link for us to review you configuration.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Manual ways for grub2:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by esc1 on 2012-08-27
Thanks for the reply. I only have the cloned drive hooked up. No ubuntu install is on either system.. it's an old system disc and frankly not sure what is on it. This is just an assignment no one can tackle at work and I appreciate the help. 

Here is my boot info: [http://paste.ubuntu.com/1170309/](http://paste.ubuntu.com/1170309/)

---

### Post by oldfred on 2012-08-27
Moved to other OS. Since it is Redhat 8.0

It looks like an old Redhat  8 install with separate /boot, /home. /var & /usr and the old 2.4 kernel. I did have Redhat 7 similarly installed 10 or 12 years ago. Not sure what old version of grub it used. Boot-Repair only works with grub2, so BootInfo is all it really can do on an old system with grub legacy.

You might try Supergrub and see if you can boot from it. Then from inside your install you can reinstall grub legacy to the MBR.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
I think you will want the older version that supports grub legacy not the newer grub2.

If you can boot then you can reinstall grub to MBR:
This is to refresh your GRUB files in /boot/grub and re-install GRUB to MBR.
sudo grub-install /dev/sda
This is to automatically generate a new menu.lst file for you.
sudo update-grub

You also may be able to chroot into your install and then run the above commands. But with all the separate partitions I am not sure of the exact commands anymore. I would think in chroot you have to mount all of them.

THis was for Ubuntu:
old 2006 instructions to reinstall grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by esc1 on 2012-08-27
Thanks for the info. I will look into that. Found out grub on the disc is .92

---

