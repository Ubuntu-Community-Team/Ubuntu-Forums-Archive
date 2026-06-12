---
title: "How to? Dual boot Windows &amp; Ubuntu 6.10 on 1 HD"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by firezip on 2006-12-27
Hello guys,

I have recently begun using Ubuntu 6.10 a few months ago on it's own separate hard drive and wish to move to a dual boot setup. The hard drive am I currently using is a 160gb  and has around 60gb left for a linux install. I am wondering on how I can accomplish this dual boot. Here are some questions

[LIST]
[*]Partitions(Which do I need to create)
[*]Will grub be an issue?(I've had grub errors every time I tried to dual boot on 1 HD)
[/LIST] 

Well thank you for your time and help :)

-firezip

---

### Post by tszanon on 2006-12-27
> **firezip said:**
> Partitions(Which do I need to create)

At least:
/ - for every file that will be created
swap - for swap space

It is recommended that you have a /home partition, so you can keep your personal files and settings apart from the system.

> **firezip said:**
> Will grub be an issue?(I've had grub errors every time I tried to dual boot on 1 HD)

Well, I've never had any issues with grub when dual-booting with just one HD. I had problems booting Windoze when using 3 HDs, but nothing that a proper configuration on /boot/grub/menu.lst couldn't solve.

---

### Post by tagra123 on 2006-12-27
> **tszanon said:**
> At least:
/ - for every file that will be created
swap - for swap space

It is recommended that you have a /home partition, so you can keep your personal files and settings apart from the system.



Well, I've never had any issues with grub when dual-booting with just one HD. I had problems booting Windoze when using 3 HDs, but nothing that a proper configuration on /boot/grub/menu.lst couldn't solve.

If you already have ubuntu working on another harddrive why not just use partimage and have grub re-install to the mbr. It will find the windows and Ubuntu and get you up and running more quickly. You can do this using the live cd or another cd such as sysrescuecd.

---

### Post by gn2 on 2006-12-27
Remember to leave 25% free space on your Windows partitions or they will not be able to defragment properly.

Have you considered virtualisation with VMWare or Parallels, if your hardware is up to the task, it has distinct advantages over dual-booting.

---

### Post by lucky_chouhan on 2006-12-27
Here is mine (Segate 80 GB)

C:\Windows Xp       (10 GB)
D:\Windows 2003    (10 GB) 
E:\Downloads         (15 GB)
F:\Torrents I           (15 GB)
G:\Torrents II         (10 GB)
ext:\Ubuntu            (15 GB)


First i am istalled windows xp, then windows 2003 and create 3 partitions (downloads, torrents I, torrents II and remain is as it is (unformated) then installed Ubuntu and select remain space for linux and install grub on my HD MBR restart and i got this menu  -

Ubuntu
Ubutnu Recovery
Other OS (windows xp, 2003)
(mine is Windows xp and windows 2003)

---

### Post by firezip on 2006-12-27
> **tagra123 said:**
> If you already have ubuntu working on another harddrive why not just use partimage and have grub re-install to the mbr. It will find the windows and Ubuntu and get you up and running more quickly. You can do this using the live cd or another cd such as sysrescuecd.

That is what I used to do with my IDE drives. I just got a new dell for Christmas and the only hard drive type it supports is SATA.

[QUOTE=gn2]Have you considered virtualisation with VMWare or Parallels, if your hardware is up to the task, it has distinct advantages over dual-booting.[/QUOTE]

Yes I have considered, but I like just having 2 separate operating systems.

--------------
Ok so here is the general idea of the partitions that I need
[LIST]
[*]/
[*]/home
[*]swap
[/LIST]

Now what boot flags do I set each one of these as?

Thanks! :D

---

### Post by gn2 on 2006-12-28
Have you tried doing it this way: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

