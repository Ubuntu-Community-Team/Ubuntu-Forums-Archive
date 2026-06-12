---
title: "SATA disk not recognized during install"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Battousai on 2006-11-09
Hello everybody.

I've been wanting to install ubuntu for a long time, but now I've got a problem...

I launch the Edgy live CD, and when I try to install, my Sata HD is not recognized.
I tried sudo fdisk -l , but nothing is found.

It is my only disk so I can't install it anywhere else.

I'm a total beginner, so sorry if I can't explain very well.

How can I make ubuntu recognize my HD?

EDIT:my HD is a Seagate ST3320820AS model

---

### Post by autocrosser on 2006-11-09
What computer/motherboard are you using? There have been reports of problems with some SATA controllers & Edgy--you might want to install Dapper instead--It is more stable than Edgy & is better suited for someone just getting into Linux.

---

### Post by Battousai on 2006-11-09
Thank you
I'm using a Fujitsu-Siemens Scaleo

CPU: Dual Core 2 E6300 
mother board : unknown but a fairly generic one.
I wanted to install Edgy since I know it's really easy to activate the second core of my CPU.

so you say it should work with Dapper? I'll try that tomorrow then.

---

### Post by Battousai on 2006-11-16
So I tried Dapper Drake
I get the same problem : my HD is not recognized by Linux.
My Mother Board is a MSI-7293 µATX. 
My CPU is still a dual core 2 E6300 and my HD is still a SATA Seagate ST3320820AS.
I looked on the net , but couldn't find anything.
When I enter fdisk , nothing is found (except my external drive)

Does someone have an answer to this?

---

### Post by ReinaDelSur on 2006-11-18
Hi, I also have the same problem as Battousai. I just majorly upgraded my computer and would like to install Ubuntu on a partition of my new SATA HDD. The Live CD runs great (though slow). However, when I click Install, Ubuntu does not detect my SATA HDD. As it is my only hard drive, I cannot install Ubuntu onto my computer, which is a pity... ](*,) 

Here's my config:
Motherboard: ASUStek P5VD2-MX
CPU: Intel Core 2 Duo E6400
HDD: Hitachi 80 Go SATA II Hard Disk
2 Go RAM

Thanks a million for your help...

Ari  ;o)

P.S.: The installation CD I have is the one for Dapper, so I guess the problem's not even about the new Edgy 6.10 version of Ubuntu...

---

### Post by AAM on 2006-11-18
I also had the same problem with the southbridge chipset on my 'new' ASUS AV8 motherboard. The problem was resolved in two ways:

1. MEPIS6 recognised the chipset out of the box, but Dapper would not. A Live DC will run without the SATA so you need to look to see if you can actually see the drive (System|Administration|Disks in Ubuntu6.06). 
2. Ubuntu 6.06.1 was supposed to fix the problem. The download did not work, but a magazine disk for 6.06.1 did.

I can only suggest that you look in the BIOS start up to find the number of the southbridge interface to SATA and then do some searching.

---

### Post by drtvasudevan on 2006-11-18
the answer is here?
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

---

### Post by ReinaDelSur on 2006-11-18
> **AAM said:**
> I also had the same problem with the southbridge chipset on my 'new' ASUS AV8 motherboard. The problem was resolved in two ways:

1. MEPIS6 recognised the chipset out of the box, but Dapper would not. A Live DC will run without the SATA so you need to look to see if you can actually see the drive (System|Administration|Disks in Ubuntu6.06).
What's MEPIS6??
If I look into System/Administration/Disks, I can see the two NTFS partitions of my hard drive, but they're treated as Unknown (one is "tmpfs" and the other is "unionfs" whatever that means) and more importantly the unformatted space I had left for Ubuntu out of the 80 Go is nowhere to be seen... :-k 
On the other hand, my old IDE Maxtor Hard Disk, which I put into a box and plugged into a USB port is recognized and Ubuntu offers to install on there!

> **AAM said:**
> 2. Ubuntu 6.06.1 was supposed to fix the problem. The download did not work, but a magazine disk for 6.06.1 did.

I can only suggest that you look in the BIOS start up to find the number of the southbridge interface to SATA and then do some searching.
I don't think a further version of Ubuntu will fix anything as Battousai reported the same problem using Edgy, which is way more recent than Dapper.
The Southbridge interface to SATA on my motherboard is: VIA VT8237A, whatever that's useful for: I don't even know what a Southbridge interface is...

Please help! Thx a million...

---

### Post by AAM on 2006-11-18
Sorry for presuming knowledge.

MEPIS6 is a KDE-based distro based on Ubuntu now that runs as a LiveCD with installer just like Ubuntu. I happened to have a copy of their most recent release and it recognised the chipset with the SATA attached and showed the drive. I have discovered that hardware recognition at the bleeding edge is very variable, so it pays to shop around.

The 'Disks" that you saw on Ubuntu are all RAM-based. Your Ubuntu is not seeing your physical hard drive (specifically Ubuntu is not recognising the chipset to which the SATA drive is connected and so thinks there is nothing there).

This may or may not be fixed in Edgy. Edgy wasn't released when I had problems, so I had to wait for 6.06.1, and I would expect all that goodness to be translated forward into Edgy and Feisty also.

The Ubuntu forums didn't seem to be too plentiful with solutions, but follow the previous link anyway as it may be a solution. 

The solutions would appear to be:


[INDENT]1. Also I would suggest trying another distro to see if you can get it recognised. Try MEPIS and/or Knoppix.

2. Reconnect your old IDE drive by USB or IDE connector and install there until the problem is fixed.
[/INDENT]

It's a bit late, and wise after the fact, but it pays to make sure that the hardware is supported before buying it. This I also learnt the hard way!

---

### Post by ReinaDelSur on 2006-11-19
Thanks for everything AAM

I actually installed Edgy, after browsing the Internet for ages trying to find something, and it works.

My problem was fixed post-Dapper: Ubuntu did not recognize the JMicron IDE + SATA controller that is on most motherboards supporting Core 2 Duo CPUs. So, depending on people, Ubuntu didn't recognize either the IDE CD-ROM drive or the SATA hard drive that was connected onto the controller.

Well, they did fix it (there were approximately 30 pages' worth of bug confirmation on Launchpad!) and now I'm running Ubuntu Edgy AMD64 and proud of it.

Thanks again for your help. I'm just starting with Linux, and I think it's not going to be that easy, even though it's real interesting and --to my mind-- worth it.

---

