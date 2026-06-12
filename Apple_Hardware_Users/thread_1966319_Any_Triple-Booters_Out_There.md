---
title: "Any Triple-Booters Out There?"
date: 2012-04-27
forum: Apple Hardware Users
---

### Post by inspiredbylasers on 2012-04-27
Windows 7/ Lion OSX, Ubuntu 12.04 LTS

No bugs encountered in Lion OSX or Windows 7

---

### Post by smurphy on 2012-05-06
Never tried it with 12.04 (installation, setup), but I was a triple booter with 8.04. Not using windows anymore though - so I use the partition for my media-data ([Tripple Boot on Mac Mini]("http://stargate.solsys.org/mod.php?mod=blog&op=view&view=174&expand=yes")).
Using dual-boot here at the moment, with 6 Partitions setup on the HD - OS-X Snow Leopard, and KUbuntu 12.04.
The Upgrade to Lion only works through external harddrive, as the installer refuses to install itself if there isn't enough space to waste for a recovery partition (tsk).

---

### Post by thinktyler on 2012-05-06
I triple boot. Works perfectly.

---

### Post by vincebs on 2012-05-06
I had OS X 10.7, Windows 7, and Ubuntu 10.04 on my computer. I tried to upgrade Ubuntu 10.04 to 12.04 but the upgrade failed because of this bug in grub:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/988583](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/988583)

So right now I'm only using OS X.

---

### Post by ammofreak on 2012-05-06
Hi ):P
Triple booted an Asus G73. OSs are Windows 7 (64), Windows 7 (32) and Ubuntu 10.04LTS. Never had a problem. Did both Window's OSs first, then linux. :)

---

### Post by oboedad55 on 2012-05-06
Three hard drives, one with Arch and KDE, one with openSUSE and KDE, one with Arch and XFCE 4.10, Ubuntu 12.04 and Fedora 16, all 64 bit. I also had Sabayon 8 on the last drive but got tired of fooling with it. Claims to be a rolling release but with updates coming only on Saturdays so Firefox 12 took two weeks to come through the pipe. Package management is unnecessarily complicated with portage, equo and equo's oddly named Sulfur Store that has only free apps. Go figure... :lolflag:

---

### Post by scognito on 2012-05-19
Triple boot + NTFS shared partition on the same hard disk.
I'm a master.:guitar:

---

### Post by N00b-un-2 on 2012-09-12
on all my computers except my HTPC which strictly runs Lion (haven't upgraded to Mountain Lion because I use the Front Row hack on Lion and deprecated iTunes for metadata stuff...).  That and my Raspberry Pi running XBMC on top of Debian.

My main desktop is a custom built ASUS P5KPL-AM EPU system with Mountain Lion 10.8.1, Windows 8 CP and Kubuntu 12.04.

My wife's desktop is a modded Dell Optiplex 320.  It runs Lion 10.7.4 (can't upgrade to ML on this one because of a 32 bit only kext needed for SATA to work... old ATI chipset).  Windows 7 and Kubuntu 12.04

My netbook runs Mountain Lion 10.8.1 with a SUBSTANTIAL amount of hacking, modded kexts and Atom kernel, Windows 7 and of course Kubuntu.

My current laptop runs Snow Leopard 10.6.8 (AMD cpu, can't be bothered to jump through hoops to get Lion or ML to run on an AMD, Snow Leopard was hard enough), Windows 8 CP and Kubuntu 12.04 with a custom built kernel and LOTS of tweaks.

I prefer to use Chimera/Chameleon to handle booting because it is very flexible and can detect bootable operating systems (like on a thumb drive) when booting from the hard drive on the fly.  Very cool

---

### Post by Maro848 on 2012-09-12
I was able to get 5 operating systems running on a spare laptop at one point because I wanted to see if I could. I installed windows 7, Arch, Fedora, Ubuntu, Backtrack, and Macbuntu to one hard drive using an extended partition setup. Ubuntu was the last one installed and I had to use a program to customize the grub menu so that I could tell all of my installs apart from one another. Not long after that I did decide to get rid of a few installs and basically go back to a dual boot of arch and ubuntu on that system.

---

### Post by wheeze on 2012-09-12
Redacted.

---

### Post by N00b-un-2 on 2012-09-12
> **scognito said:**
> Triple boot + NTFS shared partition on the same hard disk.
I'm a master.:guitar:

I've done the same thing on my systems.  I have experimented with making that 4th partition EXT2, EXT3, FAT32, HFS+ and NTFS.  As much as I hate to admit it, NTFS is just the way to go with this kind of approach.  It's fully compatible with every OS pretty much out of the box, supports journaling, is fully POSIX compliant, has no significant file size limit unlike FAT file systems, and has decent I/O performance.  It's not quite as efficient as EXT file systems and does have a nasty habit of becoming fragmented.
I like to create all of the standard XDG specified user directories (documents, downloads, music, pictures, videos) and then symlink to them in my home or user directory.  Using junctions on Windows works very well and symlinks are relatively transparent on Linux and OSX.  However actually mounting /home/user or equivalent to the same place as is used on another operating system is just asking for problems.

---

### Post by scognito on 2012-09-12
Actually I store in data partition just music, video and pictures (and I simlink them too) but /home is in the same partition of Linux.

---

### Post by opensshd on 2012-09-12
Win7 64bit, Ubuntu 12.04 64bit, openbsd 5.1 64bit \o/

---

