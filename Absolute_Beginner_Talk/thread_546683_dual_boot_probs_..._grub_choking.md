---
title: "dual boot probs ... grub choking?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by andrewbadera on 2007-09-09
hello all-

having problems dual booting XP and 7.04 ...

XP boots fine. I believe my partitions look like this:

/dev/sda1 ntfs (hd0)
/dev/sda5 fat32
/dev/sda6 ext3 / (hd0,5)
/dev/sda7 ext3 /home
the remainder is swap

I originally had grub installed to the mbr, but after reading, it sounded like xp's bootloader was the way to go. I used xp's repair console to repair my mbr. I used a livecd to get an ubuntu.bin generated for /dev/sda6 and dumped it on the share. back in xp, dropped that in c:\ and set up windows' boot settings.

I use the livecd to get a terminal, and a grub prompt. I do a find, and etc. etc. grub stuff, reinstalling, I believe, grub, now on (hd0,5)

xp continues to boot fine, but I get a blank screen when I select ubuntu. so, I reinstall ubuntu, this time specifying (hd0,5) for the grub install.

still getting a blank screen.

do I need to generate a new ubuntu.bin? I'm getting sick of waiting on the cd to boot ... I long to get back to booting ubuntu off my HDD!

thanks in advance ...

---

### Post by andrewbadera on 2007-09-09
bump ... anybody? I regenerated the boot file, still getting a blank screen here ...

---

### Post by rickycodie on 2007-09-09
i think that the problem is that the grub needs to be installed on (hd0,0).  what is on your fat32 partition?

---

### Post by andrewbadera on 2007-09-09
> **rickycodie said:**
> i think that the problem is that the grub needs to be installed on (hd0,0).  what is on your fat32 partition?

that fat32 is just for the share, it's a new 400gb drive, fresh xp and fresh ubuntu installs.

why would grub have to be in the mbr? I thought that was optional. I want the xp bootloader to be primary.

---

### Post by rickycodie on 2007-09-09
i could be wrong as a rule i keep my partitions a simple as possible.i use ntfs3g to mount my ntfs partitions. that's the easiest thing for me.

---

### Post by andrewbadera on 2007-09-11
Still working through this .. I ended up going back to all primary partitions though. I was dual booting, but couldn't get VM running ... definitely in better shape now though.

---

### Post by soma4me on 2007-09-11
andrewbadera,

Hi, I also have dual boot setup on multiple machines:

[LIST=1]
[*]Ubuntu 6.06/Win2K - Two IDE hard disks, Ubuntu on 2nd disk, GRUB written to mbr of Win2K disk.
[*]Ubuntu 6.06/WinXP - Two IDE hard disks, Ubuntu on 2nd disk, GRUB written to mbr of WinXP disk.
[*]Feisty Fawn/Vista - Two SATA hard disks, Ubuntu on 1st disk, GRUB written to mbr of Ubuntu disk.
[/LIST]

The first 2 installed and run without any issues, the 3rd caused me a bit of headache, but I was able to use the information and SuperGRUB disk from the following web site to resolved it.    You may want to take a peak.

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

As you can see, I use GRUB in all cases, it is much friendlier to Windows then XP bootloader to other breeds of OS.

Just my opinion, hope this help.

---

### Post by Terl on 2007-09-11
I agree with soma4me, stick with Grub.  I have never had any issues with Grub booting windowsXP for me and I have used it to boot as many as 4 linux distros and windows as well.

---

