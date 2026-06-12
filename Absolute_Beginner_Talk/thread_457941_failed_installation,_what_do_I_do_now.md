---
title: "failed installation, what do I do now?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by holymuffins on 2007-05-29
Alright, well I started to install ubuntu (6.06) in the free space I had. The Problem is, I wanted to do a little more research on ubuntu before I installed it, so i decided stop in in the middle of the installation. Now when I try and boot up my comuter, i get the message "error loading operating system." My assumption is that something in the partialy installed partition is telling the computer to boot it, but it is incomplete so it can't. Can anyone tell me how to change it so that my computer will not boot to the partialy completed ubuntu? The tools I have to do that are BIOS and the ubuntu live CD (which I'm using now). Thanks in advance.

---

### Post by apjone on 2007-05-29
So you have no widows disc? The only thing I could recomened is restarting and completing the ubunut install. Or using recovery console from windows XP install disc and fix the master boot record

---

### Post by Pobega on 2007-05-29
The best thing you could do right now is reinstall Ubuntu from the liveCD. Stopping an installation midway isn't really a smart idea, and hopefully you didn't cause any permanent damage to your hardware (It's highly unlikely, but still a possibility).

I'd install Ubuntu, then burn a WinXP disc (If you need WindowsXP still) and dual-boot.

---

### Post by holymuffins on 2007-05-29
I have a windows disc, but what I was hoping was possible is for me to get rid of the half installed ubuntu, or realy do anything so that the computer will try and boot windows instead of ubuntu, with all my files intact.

---

### Post by EdThaSlayer on 2007-05-29
It isn't very smart to just install half of Ubuntu and then quit. It seems that you have the grub bootloader installed but you still don't have the Ubuntu terminal. I would recommend reinstalling Ubuntu over that broken partition and then rebooting your pc.

---

### Post by holymuffins on 2007-05-29
Would it be possible for me to set up a dual boot without destroying all the files and settings I have on my computer now? Could I reinstall Ubuntu in the broken partition and set up a dual boot with windows already on my computer?

---

### Post by zvacet on 2007-05-29
Yes,you can reinstall.When you get to the partition point select manual and you will see  all yours partitions.Delete ext3 and make it unallocated space.Now you have free space to install Ubuntu.How will you make partitions depends on you.You can try this

1. root =10GB                  mountpoint  /
2.swap =2xRAM
3. home = rest of free space  mountpoint /home

Second way to delete existing ext3 partition is to download Gparted live CD.It is good tool and maybe you will need it in the future if you want to resize existing partitions.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

