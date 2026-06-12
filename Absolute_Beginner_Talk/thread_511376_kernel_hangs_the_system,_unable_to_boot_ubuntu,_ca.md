---
title: "kernel hangs the system, unable to boot ubuntu, can anyone help?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Kaiva Azure on 2007-07-27
**What I want to do:**
Dual boot with XP and Ubuntu without affecting my current yet unstable installation of XP and current collection of files (games and whatnot, non linux compatible games to be exact :( )

**My system:**
HP Pavilion a705w With upgrades: nVidia GeForce FX 5500, Seagate 80 gig HD (now used as master) XP pro, due to the death of XP home (explained later)

40 gig ST340015A Seagate HD
Came with the system and i am unable to install an OS on this drive, no one I know can figure out why I suspect it is due to partition magic which had a number of errors during partitioning of this particular drive... or the drive is just dying for some reason.

80 gig ST380011A Seagate HD
Contains an empty 5 gig partition meant for Ubuntu, which is leftover from a previous attempt to install ubuntu, Use of Partition magic hid the recovery partition and my recovery CDs were ineffective due to improper storage (CD note-books are worthless btw) leaving the system dead but ready for a new OS, I now have XP pro installed thanks to a friend.

All drives/partitions are NTFS I can't seem to install and OS on the 40 gig, I suspect I will need to find a stable reliable SAFE partitioning tool to make a 15 gig partition for ubuntu, I will not use Partition magic again, it already failed once I'm not giving it another chance.

Patition info:
Drive C: 71398 MB, NTFS, located on 80 gig drive, XP pro installed
Drive D: 38154 MB, NTFS, located on 40 gig drive, has unknown conflict with install of XP suspected to be failing.
Drive E: 4918 MB, NTFS, located on 80 gig drive

512 RAM

Intel Celeron 2.93 Ghz

**My Problem:**
I have the Feisty Fawn x86 Live CD, I set it in my CD try and reboot the system, I can boot the CD and reach the menu with options on starting Ubuntu, No matter what option I choose I eventually get a system hang.

I choose "install or start Ubuntu" and I get as far as seeing text mention something about initializing/booting the kernel and then the system will hang, and at the bottom of the screen I will get two lines of text like this:

Int 14: CR2 df000000 err 00000000 EIP c020c384 CS 00000060flags 00010007
Stack: c00f7da0 c03f129b c0371d8c 00000002 c00f7da9 000f7da0 00000000 00000000

*EDIT: I probably should have mentioned I have tired the Live CD, Instalux, and Wubi and all three methods end with the same resulting issue, So I don't suspect it is a problem with the Live CD.*

I have no idea what that is but something like this pops up any time I try to install Ubuntu, I think this is occurring during the kernel process, I cant get Ubuntu to boot on this machine whatsoever, please keep in mind that I really don't understand Computers as well as I might seem to, so please have patience with me, I might ask some very retarded questions to make sure I understand what I'm being told ^ ^;;

If I missed anything or if my exact issue is covered in another thread, please let me know. I did my best to make sure there wasn't another thread but then again I know very few terms well enough to have searched properly :(

---

### Post by trent dillman on 2007-07-27
...

---

### Post by Kaiva Azure on 2007-07-27
> **trent dillman said:**
> try booting with the alternate cd, and/or damn small linux and report back

maybe it's a live cd bug?

I probably should have mentioned I have tired the Live CD, Instalux, and Wubi and all three methods end with the same resulting issue, So I don't suspect it is a problem with the Live CD. I will have to order the alt CD since my attempts to burn any .iso end with a brand new reflective Frisbee :D I have plenty of those already O_o

Do you still want me to try Damn Small Linux? It seems to require that I make a partition but I'm afraid to try that with just any partition program since Partition magic had already crippled my system before, I would need recommendations for another partitioning program if possible. :cry:

---

### Post by tormod on 2007-07-29
Please follow up in bug #128421 [https://bugs.launchpad.net/bugs/128421](https://bugs.launchpad.net/bugs/128421)

---

### Post by tormod on 2007-07-29
Is that nVidia card a PCI card?

---

### Post by Githlar on 2007-07-29
I have an HP a705w also. Boot the kernel with the acpi=off option. When using the Live CD/DVD at the boot menu, press F6 and then add "acpi=off" to the end of the line.

---

### Post by cavaliercrazy on 2007-08-23
The acpi-off helped me out quite a bit. 

however when i booted with that option. the loading went through i got the ubuntu loading screen. and the it kept scanning these files. i couldnt tell what the where. becasue they were flying by too fast. 

so i late the scanning run and an hour later it was still going with no disk activity and no hardrive activity. so i ended up. just goign back windows that night. and to see if i could find any more info on this. 

any help is appreciated. thx.

---

### Post by cavaliercrazy on 2007-08-23
im also using a hp a614n.

---

### Post by Akt on 2007-09-28
Hi, Kaiva came to my house and this solution worked for him.  Many thanks!!!!!

---

### Post by Kaiva Azure on 2007-09-29
Posting with Firefox from a HP Pavilion a705w :mrgreen:
WINDOWS = SLAYED :twisted:
Thankies Akt :3

---

