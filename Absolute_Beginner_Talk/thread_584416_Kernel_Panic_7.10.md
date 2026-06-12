---
title: "Kernel Panic 7.10"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by deadgobby on 2007-10-21
Cannot boot after upgrade from 7.04 to 7.10 I am getting
24.720279 kernel panic-not syncing: vfs: unable to mount root fs on unknown-block(0.0)

Help would be very helpful.

Gobby

---

### Post by deadgobby on 2007-10-21
bump

---

### Post by deadgobby on 2007-10-21
Any one?

---

### Post by chewearn on 2007-10-21
hi deadgobby
I kept your thread on watch, but refrained from replying, because I have only a partial knowledge here; but I did encounter this error before (in another non-ubuntu setup), so I know a little bit about the problem.

Basically, the linux kernel is not able to find your root directory.  There could be a number of reasons why this is so; a few possibilities that I know are:
1. your /boot/grub/menu.lst kernel parameter for root might be incorrect
2. your kernel might not be compiled with the correctly filesystem support; or the required filesystem module is missing
3. /boot/grub/system.map might be incorrect

If you googled for "vfs unknown block" there are a number of pages about it.

Else you can also post the menu.lst, system.map and fstab files here; also output of sudo fdisk -l

---

### Post by PreviousN on 2007-10-21
I had this problem when I upgraded too. Its an easy fix. Press esc when booting to go to the grub menu. Choose the old kernel (safe mode or whatever) (safe or not I don't care. we just need to get to a root terminal).

After you get to a root terminal (either open a terminal in gnome and type "sudo -i" or go into the safeish mode from grub)
Do a "apt-get upgrade"
likely it'll tell you an error message. 
On my installation the problem the message was something like "upgrade interrupted, run this:
"dpkg --configure -a""....so I ran that. 

after that, I ran a "apt-get upgrade -d" (I think that was the command. Basically try to reupgrade your system). Then I rebooted and everything worked. 

Hit me back if none of this works for you.

---

### Post by deadgobby on 2007-10-21
Thank very much for your help. OK stuck agian

ran 
apt-get upgrade -d
>error run -f

apt-get upgrade -f

>error
unpacking replacement python2.5-minimal errors were encontered while processing 
/var/cache/apt/archives/libgnomeuvfs2-commen_1%3a2.20.0.0=0ubuntu_all.deb

ran

dpkg --configure -a

>error
dpkg: dependency problem prevent configuration of libgtkhtm13.14-19 = depends on libgnomeui-0(>=2.19.1);depends  libsgnomevfs2-0(>=1:2.17.29) however package libsnomunui-0 is not configure yet


I wrote this down and I hope I did not leave any detail out. I cannot run dpkg --configure -a it just loops agian.

thanks for your help

got some sleep too

Gobby

---

### Post by PreviousN on 2007-10-21
ok. So does this mean that you were able to log in fully with gui to get to a root terminal, or did you use the safe mode? 

If you got into GNOME, then do this:
System --> Administration --> Synaptic --> Edit --> Fix Broken packages --> Apply --> Edit --> mark all upgrades--> Apply. 

Fix broken packages fixes dependency problems. By the way apt-get upgrade -f (I think) means that it will fix dependency problems using apt...but I could be wrong.

After all that, I would recommend two things:

1. Try restarting into the new kernel. Maybe it boots. If not, go back to safe mode. 
2. If you're back in safe mode, type "sudo apt-get install -f libsgnomevfs2-0" 

(libsgnomevfs is the package it first says you're missing). Also, you may try "apt-get --reinstall libsgnomevfs2-0".

---

### Post by deadgobby on 2007-10-21
cripes I would to have a gui right now. try it and see what happens...:lolflag: Just got to laugh

---

### Post by deadgobby on 2007-10-21
This is what I did. At least I save every thing or back up to my slave drive. Reinstalled 7.04 and upgraded from it. I think it may be the low lanancey kernel that I installed trying to get Ubuntu  Studio to work.

---

