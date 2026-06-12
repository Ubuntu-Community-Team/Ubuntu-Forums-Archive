---
title: "Ubuntu with Windows on one partition??"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by Waqas on 2005-09-07
Hi fellows.. :)

I have one HD, with 2 partitions; c:/ & d:/. C: installed with Windows. I was informed that Ubuntu allows dual boot or dual OS. Im an absolute new to Linux, since I was born with Windows.. so, can I share one partition for Windows & Ubuntu? Or should I install Ubuntu on my D:/ ?? Will Ubuntu format everything, and the most important thing, will Ubuntu recognize NTFS??  :neutral: 

And can you guys kindly point me to where to start.. ??  :grin: Because I tried the live CD and its promising. I think I can move to this OS, and stop piracy..  :-#

---

### Post by aysiu on 2005-09-08
NTFS: Read ok. Write not okay.
Dual-boot: Easy if you put Ubuntu over the D:
A little more complicated if you want to share files with Windows.
You'd need a separate FAT32 partition.

---

### Post by Waqas on 2005-09-08
Thank you very much for replying..

But where can I start? I need something to refer before installing.. :)

---

### Post by aysiu on 2005-09-08
[http://www.ubuntuforums.org/showthread.php?t=13042&highlight=dual+boot](http://www.ubuntuforums.org/showthread.php?t=13042&highlight=dual+boot)

---

### Post by wvslkr on 2005-09-08
Hopefully this will help [https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

---

### Post by poofyhairguy on 2005-09-08
[http://www.tipmonkies.com/2005/06/23/linux-filesystems-and-partitioning-a-primer/](http://www.tipmonkies.com/2005/06/23/linux-filesystems-and-partitioning-a-primer/)

There is a great resource.

---

### Post by Waqas on 2005-09-08
Thank you again.. I think that will do.

But if Im going to get a new HD, it will be much easier right?? I dont need to repartition with gparted.. right?

---

### Post by wellery on 2005-09-08
[QUOTE=Waqas]Thank you again.. I think that will do.

But if Im going to get a new HD, it will be much easier right?? I dont need to repartition with gparted.. right?[/QUOTE]

Yes that's right. You can just get the installer to install to the new hard drive and it will create the partitions that it needs.

---

### Post by Waqas on 2005-09-08
Ok then.. Ill give it a shot tonight.. I printed about 60 pages of tutorials already!!!

---

### Post by Waqas on 2005-09-10
[QUOTE=wellery]Yes that's right. You can just get the installer to install to the new hard drive and it will create the partitions that it needs.[/QUOTE]
Hello guys.. 

Err.. installation succeed in 5-6th times already, but dual booting still not funtioning. Heres the case..

I have 2 HDs. Old one with WinXP, new 80gb shining one for shiny Ubuntu. So, I partitioned the second HD with Ubuntu partitioner as below:-

1 - Primary | 25gb | bootable | ext3 | /
2 - Logical | 1.5gb | swap
3 - Logical | 58.5gb | fat32 | /share

I can see my first HD while partitioning, and luckily no harm done to it. But, GRUB installed and overide my MBR, then both OSes failed to boot. I managed to run WinXP Recovery System and ran mbrfix. WinXP can boot now, but Ubuntu cant. So, I reinstalled Ubuntu after unplugged the 1st HD, so it build it's dependant MBR.  ](*,) 

My only choice now is to select booting HD via BIOS.. kinda annoying. 

I followed instruction on how to installed Ubuntu on existing WinXP, but that thread only explain how to do it in one HD (requires 3rd party partitioner). So I wonder if I missed something here since Im doing it on seperate HD.. can someone walk me through it briefly..??  ;-)

Anyway, so far so good.. I managed to leard sudo commands and its very fun. Im zero on programming, but thanks to developer for tonnes of help on the internet.

---

### Post by David Marrs on 2005-09-10
You probably moved your MBR to your Linux partition when you should have left it on the Windows partition. The Ubuntu installer's not very clear about that point. You should be able to fix the problem by starting your computer with the installation CD in the drive and then edit the grub configuration file to make sure that the (I think it's called) active partition is the windows one - if that's indeed the problem. I don't know how to do that, but the answer will be in the grub documentation.

Yes, the learning curve is particularly steep when something goes wrong. :p  Thankfully, maintaining a Linux system is far easier than setting it up. :)

---

