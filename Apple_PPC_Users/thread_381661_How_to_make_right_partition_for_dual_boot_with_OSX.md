---
title: "How to make right partition for dual boot with OSX?"
date: 2007-03-11
forum: Apple PPC Users
---

### Post by kiethrios on 2007-03-11
I have an iBook G4 1,2GHz. However, i just only have 30GB hardisk.

These days, i have been looking how to install the ubuntu in iBook and make a dual boot system with Mac OS X.

I've tried desktop cd and alternative cd.

however, neither of these work.

i still have the problems on making partition. As a result, i formatted my hardisk, and now i am using the live cd to post my question.

i use the GNOME Partition Editor to view my hardisk, i found that:
Partition        Filesystem        Size
/dev/hda1        unknown        31.5 KiB
unallocated        unallocated        128.00 MiB
/dev/hda3        hfs+        27.82 GiB

yet, i haven't install Mac OS X since this afternoon when i installed the alternative cd with the partition described below: 
/dev/hda1      31.5 KiB      Apple
/dev/hda2        128.00 MiB        bootstrap
/dev/hda3       19 GiB        HFS+    (OSX installed)
/dev/hda4       1 GiB       swap
/dev/hda5       9 GiB       Ubuntu (wanted to installed but failed)

then the ubuntu start to install, but when it came to the "software installation" part, it stop at 92% for almost 1 hours, i don't know what had happened, and i press the power button of the iBook and then when i just wanted to log in OSX, it appear a block icon on the screen.

i don't know what to do and formatted the hardisk and just make it like what it used to be with no system installed.

i don't know whether my partition is wrong, can anybody help me?

thanks, my friends.

---

### Post by bodek on 2007-03-11
Hi,
I will tell you what I did when installing dapper.
Just boot from the OSX install disk. When the setup starts, go to tools (?)|disk utility and there set the partitions: divide the disk in two partitions according to your liking, partition the second one with HSF+ and the first leave as empty space (you can click the little padlocks to prevent changes to the sizes). 
Then continue installing OSX (on the second partition). After everyting is set up and OSX works, reboot with the live CD.
When you come to partitioning let the installer use the bigest empty space. It will ensure that the bootstrap partition is created properly and the others are also set up.
hope this helps

---

### Post by grazie on 2007-03-12
It looks like the Ubuntu install failed for some reason. I don't why for certain, but installing the language packs has been know to cause problems. You could try installing Ubuntu again and skip the language packs which can be installed later. If the install gets stuck again it can usually be sorted. I suggest you logon to one of the IRC channels on irc.freenode.net and explain your problem. The #ubuntu channel is nearly always very busy, so you may have more luck with #kubuntu or #xubuntu.

---

### Post by kiethrios on 2007-03-12
thanks, my friends.

i've been finished the installation last night after i tried to make it work all day.

i think the problem of installation when i choose the language support. after i finished the installation, i found that very slow to upgrade my ubuntu, and it took me almost two hours with install the language support yet.

i now using the partition like that: when i first install OSX, i make two partition with the OSX installation dvd and launched the disk utility, then i choose two partition and modified the spaces of them with which the first is 20GB and the other is 10GB.

then i installed the OSX on the first partition. then i used the alternative cd to install the ubuntu.

i deleted the second HFS+ partition that are made by the disk utility of the OSX installation dvd. as a result the partitioner of the program of installation of ubuntu regarded it as "free space". after that i choose the command "use the largest continued space", and the program make two partition for me automatically. then the program continued, and the rest of the installation took about 40 minutes. then i come to the welcome screen and type my user name and password...

yet, i stiil haven't get the language support and the right method of input.:lolflag:

---

### Post by arkstfan on 2007-03-12
Well after mucking around trying to install on my firewire drive, I gave up. I used carbon copy cloner to copy my internal hard drive to the firewire, set it as my boot drive, restarted OS X and then used disk utility to partition the internal hard drive. I formatted most of the drive OS X journaled and left about 20 gigabytes as free space in a second partition (free space is an option in disk utility).

Dumped the contents of the firewire drive back on the internal, reset the start-up drive to the internal and restarted and all was well. 

Put the install CD into the slot, told the iMac to restart, held down the "c" button to boot from the CD, started the install program and told it to use the largest free space, it partitioned that into two partitions, and installed just fine.

I still don't know squat about what I'm doing but I can dual boot by holding down the option key  at start and it seems to work fine.

---

