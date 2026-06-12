---
title: "Help dual booting Ubuntu"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Kersus on 2006-03-13
Heya,  

Here's my situation.

I currently dual boot Xandros 2.0 and Windows XP.
Xandros was my first foray into Linux and while I liked the OS, I never realized how much I needed sound in an OS.  It wouldn't work with my Asus sound integrated MLB.  Even 3.0 apparently has the same issue.

For a long time I've been wanting to get into Linux, but finding the right distro is not easy.  Then recently I saw the Ubuntu CDs available at my workplace and grabbed one.

So I'd like to install Ubuntu over my Xandros installation.  It'll be hard to let Xandros go, but without sound its just not going to replace windows in the long run.  

I have two Hard Drives

Main drive: 
40G Xandros OS partition
50G NTFS XP OS partition
30G FAT Partition (mostly filled with programs for XP)

Secopndary Drive:
40G NTFS - all my important information

The Xandros partition comes up as something like reiser....
Ubuntu's partition program comes up but I have no idea what to do.  I do not want to lose any other info, but want to replace Xandros with Ubuntu.

I'm currently using the boot loader that comes with Xandros 2.0 and have no idea which boot loader to pick from Ubuntu's choices.  Currently I'll want it to default to XP, but allow me a chance to pick Ubuntu on bootup.

Anyhow, any help, or direction to a step by step guide would be great.  Keep in mind partitions are already there, and I need to know what to do with my current situation.... And whether or not I need a seperate swap partition...  I could have sworn I had one with Xandros but it doesn't show in the Ubuntu partition program.  

Kersus

---

### Post by TrendyDark on 2006-03-13
Dual booting can be a bit scarey, I'm doing it and luckly, it's not that hard. I'll first suggest that you use the FAT32 partition you have to store any data from Xandros you'd like to keep. Drivers & etc will have to be reinstalled, but it wouldn't hurt to compile some guide and such you'll need once you have Ubuntu up and running.

[http://www.ubuntuguide.org](http://www.ubuntuguide.org) is a good resource for some simple things.

Then, once you're done with that, in the ubuntu partition program select the Xandros partition. Delete it & it probably wouldn't hurt to delete the swap partition it has unless it's located out of order (meaning it's not right above or below the xandros partition on the list). Then you'll want to create a new partition in the free space, I suggest using the "Automatic" option (guided partitioning). 

The boot loader that Ubuntu will install is GRUB. Nothing fancy looking, kind of all text based. It will put Windows XP on the list, but Ubuntu will be the default. You can always change this by editing the grub menu (the location escapes me or i'd give you a command to use).

---

### Post by aysiu on 2006-03-13
Before you embark on the Ubuntu journey, please obtain a Ubuntu live CD and boot it on your computer. Make sure Ubuntu recognizes your sound before you install it. Hardware detection should be your #1 priority when selecting a Linux OS.

After that, this dual boot guide may come in handy:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

It assumes you need to shrink your Windows partition before installing Ubuntu, but you can skip the shrinking part and just follow the rest of the instructions.

---

### Post by TrendyDark on 2006-03-13
aysiu, you're just full of fun information and sites man lol

---

### Post by aysiu on 2006-03-13
[QUOTE=TrendyDark]aysiu, you're just full of fun information and sites man lol[/QUOTE] Believe it or not, I actually bookmark good sites as they come up, and I have a huge list of helpful Linux websites in my bookmarks folder.

---

### Post by Kersus on 2006-03-13
Will Grub automatically replace (remove) the Xandros boot loader?

Oh, and yeah I tried the LIVE CD first ;)  Sound was the first thing I went out of my way to check.

---

### Post by aysiu on 2006-03-13
At a certain point, you'll be asked whether you want to install Grub to the MBR. Say "yes," and it'll replace Xandros' Lilo.

---

### Post by TrendyDark on 2006-03-13
[QUOTE=aysiu]Believe it or not, I actually bookmark good sites as they come up, and I have a huge list of helpful Linux websites in my bookmarks folder.[/QUOTE]

I used to do that, but in all my noob-ness i keep having to reinstall lol

---

### Post by Kersus on 2006-03-13
So I removed the Xandros partition, and automatically created a new one (and a swap part was created too).

It gets to 33% and then says it cannot install the file system.  I tried twice, then I removed the partition again, and recreated, and got the same error at 33%.

:confused: 

K

---

### Post by TrendyDark on 2006-03-13
is this during the installation of the system or when it's creating the new partition?

---

### Post by Kersus on 2006-03-14
Its before installing the boot loader...

I make the partition , it does a few things and gets stuck where it says its installing the file system.

:confused:

---

