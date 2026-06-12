---
title: "Blue &amp; White W/ 2 Drives"
date: 2005-07-10
forum: Apple PPC Users
---

### Post by trace594 on 2005-07-10
Ok, i have researched this problem for about 2 days now and still can't find an answer. I have a rev 2 B/W G3 400Mhz with two 80gb hard drives installed. i have Mac os X on one 80 GB HD and want to have ubuntu(5.04) on the other. The install goes through fine but when i reboot i don't even get to stage 2.  Yaboot load up and then i get the following:

/pci@80000000/pci-bridge@d/pci-ata@1/@0/disk@1:, \\yaboot.conf: unable to open file, invalid device Can't open config file
Welcome to yaboot version 1.3.13
enter "help" to get some basic usage information
Boot:


I looked this up for two days now and i can't find the solution. I have found where people have asked about the problem but no responses. I believe it has something to do about the drives not being "labeled" right during the install. well, i have hit a wall  ](*,) with this one. any help or work around would to of great help. I have thought about just using one drive and partitioning but i'm not sure. 

i have tryed the solution here:
[http://www.ubuntuforums.org/showthread.php?t=8050&page=2&pp=10&highlight=429+initrd](http://www.ubuntuforums.org/showthread.php?t=8050&page=2&pp=10&highlight=429+initrd)
but that still didn't help. 


thanks for any suggestions.

---

### Post by trace594 on 2005-07-10
Well i figured it out it seems that if you install with only one drive in the computer then you can just edit the yaboot.conf with the second drive(this is were mac os x is installed)

the only thing that was funny about it was that it had to be master to work

---

