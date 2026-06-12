---
title: "Installing Ubuntu on a Second Drive"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-06-19
I just tried a Unbuntu 7.04 Live CD and boy I'm hooked now....... Of course I still have the MS programs that can't run on Linux so I need them both.  I plan to use Ubuntu as my main OS and switch over as needed.  Here is my question.

I have a Windows XP installation and I would just like to put Ubuntu on a second drive and be able to choose once I Boot the PC up.  Is this possible?

When I built this PC I didn't want to spend a lot of money on the HD so I just have a 40 Gig that only has about 8 gigs free on the C: Drive. I have it partitioned into C: and D:
My OS is on C: and my Programs are on D:

Would it be hard to do what I am asking.  I have an old Maxtor 40 laying here as we speak.
I'd love to put Ubuntu on it and be able to choose which OS I want to run..... 

Thanks

---

### Post by maddot on 2007-06-19
it's easy... those extra partitions won't matter. Pop your old maxtor(psst...i'm using an old seagate 2gig hdd ^___^) in...link up the cables... then pop in your live cd. It should load up... and you're good to go

click on the install icon on your desktop, then go through the processes. Locations and stuff. Finally when it comes to partitions, click on guided something..(can't remember) it's the one with the radio button for other hard disk devices. 

It should auto partition the hard disk...when it's setting up grub(grub is the "selector" you're talking about) will be installed....reboot..removecd...that's it :)...all done.

---

### Post by p_quarles on 2007-06-19
Shouldn't be difficult at all. Once you get the second HDD installed and running, you should be able to run from the live CD, install, and then choose the drive you want to place Ubuntu on. Give it a try, and if you have any problems, come back here and describe them.

---

### Post by w4ett on 2007-06-19
Exactly the same installation that I have....2 drives give you much more flexibility and peace of mind.  Load grub on the master and Ubuntu on you slave drive,  this will save any problems with re-partitiong.   The live CD gparted makes this a breeze.

---

### Post by stalkingwolf on 2007-06-19
The guided setup will give you 2 partitions, the / (root) partition and the swap partition.  When I set mine
up I followed the advice found several places on this forum and added a third partition /Home.  In this way
all of your "addons can be saved in the home partition and not disturbed if you have to reinstall as I recall.

---

### Post by franck3d on 2007-06-19
absolutely, this just what I did a few weeks ago!
grub will be written to the mbr and you just choose your OS at boot!

---

### Post by Orbital75 on 2007-06-19
Is there anyway I could install to a second drive and edit the Boot.ini file to make Windows see the other OS on the other drive. Is Grub a must...... Never done this before so you will have to forgive me if these are unattainable methods....

I just figured you could put a line in Windows to point to the Boot record of the second drive.
:-)

Thanks guys for the info.

---

### Post by confused57 on 2007-06-19
> **Orbital75 said:**
> Is there anyway I could install to a second drive and edit the Boot.ini file to make Windows see the other OS on the other drive. Is Grub a must...... Never done this before so you will have to forgive me if these are unattainable methods....

I just figured you could put a line in Windows to point to the Boot record of the second drive.
:-)

Thanks guys for the info.
Here's another option:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Grub isn't installed to your Windows drive's mbr, but you can boot Windows from grub.

---

### Post by willl on 2007-06-19
> **Orbital75 said:**
> Is there anyway I could install to a second drive and edit the Boot.ini file to make Windows see the other OS on the other drive. Is Grub a must...... Never done this before so you will have to forgive me if these are unattainable methods....

I just figured you could put a line in Windows to point to the Boot record of the second drive.
:-)

Thanks guys for the info.

There is a program called Bootpart that allows you to manually add partitions to the windows boot menu, including linux ones. I haven't used this with Ubuntu, but I successfully set up an XP/Debian dual boot system consisting of 2 hard drives. There are howto's out there on how to use it. It was quick and easy.

---

### Post by Orbital75 on 2007-06-25
Thanks everyone,  I'll try one of those suggestions...

---

### Post by ottawaexec on 2007-12-09
> **w4ett said:**
> Exactly the same installation that I have....2 drives give you much more flexibility and peace of mind.  Load grub on the master and Ubuntu on you slave drive,  this will save any problems with re-partitiong.   The live CD gparted makes this a breeze.

This sounds like the answer to my problem.
Just got Ubuntu 7.10 at an OCLUG meeting this past week and installed it to an F drive.
Using an older computer that has only a 4 GB C drive; the newer F drive has 160 GB
During installation, I was offered choices as to installation site and partitioning. I picked my larger F drive, with no partition. I was informed that all info and programs would be errased, but I guess that only applies to the drive chosen.
My C drive has windows 2000 and applications.
When I start up, I just get Windows, can't get Ubuntu.
Your comment seeems to say I have to copy a file called "grub" to my c drive. is that correct?
I don't care if I lose everything on the c drive as I want this computer dedicated to Linux so that I can give it an honest try.
I have to admit, during the installation I felt good about what I was doing for the first time in over 12 years. Way back then I could build my own menu, use dos commands to do things quickly, etc.. Since then I seem to be constantly fight the programs.

So is "grub" the answer? Or can I physically switch plugs to make my newer drive the c drive?
(As you can see, I have big gaps in my computer knowledge - "A little knowledge can be a dangerous thing"
Thanks for your patience in hearing me out, and for any help.

Ottawaexec

---

