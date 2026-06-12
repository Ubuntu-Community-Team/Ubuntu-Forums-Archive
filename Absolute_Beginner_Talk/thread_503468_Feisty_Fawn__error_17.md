---
title: "Feisty Fawn  error 17"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by gasnmyveins on 2007-07-17
I just loaded Feisty Fawn. When I try to start the computer, I get this. Grub loading.... error 17.   There were no errors on my disc.
 Can anybody help me with this? Thanks.

---

### Post by FleetAdmiral74 on 2007-07-17
Here is a previous thread on this error

[http://www.linuxforums.org/forum/slackware-linux-help/54246-grub-error-17-a.html](http://www.linuxforums.org/forum/slackware-linux-help/54246-grub-error-17-a.html)

Note, this was on slackware, but the solution should be the same, or very close.

---

### Post by houstonbofh on 2007-07-17
My brother gets this on the exact same hardware I have.  The odd part is that I do not have this issue at all, and I reinstall my machine frequently.  Anyway, I am going out there with a Super Grub Disk, and will try playing with that.  Some links...

[http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by gasnmyveins on 2007-07-17
I wish I knew what half of those things mean. I'm just starting, and don't know a lot of the terms.
 Could it have anything to do with the fact that I followed the recommendation it gave me during install and only used 1/2 of my drive? 
 Do you think it would help to reinstall it and use the whole drive?

---

### Post by gasnmyveins on 2007-07-18
I started looking around and found the partition editor. It says neither of the partitions on my drive are mounted. Is this because I'm running on the live cd, or could it be part of my problem?

---

### Post by houstonbofh on 2007-07-19
The partitions are not mounted by the Live CD, unless you make a real effort to do so.  Have you tried the Super Grub Disk?  Usually it can boot a broken system...  From here...
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)
> You will need Super GRUB Disk to boot Linux for you so that you can easily check and repair your operating system's entry in menu.lst.
Super GRUB can boot your operating system by symlinks to the kernel if you use, from the Main Menu,--> Boot Gnu/Linux and  Other OSes --> Boot Gnu/Linux -->...

If you have used hard disk partitioning software recently and you have copied and pasted your partition that contains GRUB, it probably has a different partition number now than it had before. You can use Super GRUB Disk to re-install GRUB. You will also need to edit /etc/fstab if your partition numbers have changed.

If you tried the solutions above and it does nothing helped, try this solution posted in to Ubuntu Web Forums by AmericanYellow, here is the link, Grub error 17
(Make sure your hard disks are properly detected in your BIOS and set to AUTO, (not LBA, large or normal). Thanks AmericanYellow for that information.
The link referred to is [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by user1397 on 2007-07-19
You probably don't need the super grub disk right now.  You could use your ubuntu live (desktop) cd to reinstall grub, using these directions: [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by jombeewoof on 2007-07-19
just a thought, 

some bioses have the ability to change the hard drive order. In the bios you can change what is drive 1 drive 2 etc... 
If your bios does this, and you have it set weird then grub will act strange.

make sure you're set up right 
then boot to your live cd and make sure /boot/grub/menu.lst has an entry similar to this:

```
title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=110179ac-11d7-47e1-9265-25e07c3454c2 ro single initrd  
```

hd 1,0 here is my primary slave partition 1 or /dev/hdb1
if your system is on primary master partition 1 it would be hd 0,1

hardware starts at 0 software (partitions) starts at 1  (basic rule of thumb when counting in computer)

---

