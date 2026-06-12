---
title: "REQ: Installation with XP"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Epiphyte on 2007-11-27
First - I'm a complete novice to Linux / Ubuntu.

I want to install Ubuntu 7.10 onto a machine that already has XP installed.

It is configured with 2 physical hard drives as follows:

Disc 0:  Logical drive C [Windows XP] |  Logical Drive D [Temp data] - Total capacity 80 Gb; 40 Gb each
Disc 1:  Logical Drive E [Working Data] - Total capacity 250 Gb

All are NTFS configured.

I intend to put Ubuntu 7.10 onto the Logical Drive D. 

How best should I prepare the drive before commencing the installation? Do I make Drive D a Primary Partitiion? Do I need to reformat the partition  first or will the Live CD allow me to do that? :confused:

Any help or links to existing threads would be greatly appreciated.:-k

---

### Post by PmDematagoda on 2007-11-27
You should be able to install Ubuntu on drive D without much of a problem and yes, the drive will have to be formatted and the Ubuntu installer will do that for you. But one thing must be done.

When you get to the partitioning part of the Ubuntu installation you will have to select the manual method, once there, delete the partition of drive D and remake it according to these specifications:-

1) a Swap partition based on the amount of RAM you have, if you have 512Mb then about 1Gb would be enough, if you have about 1Gb or RAM then about 512Mb of Swap space would be enough.

2) The rest for the / or root directory which may be of the following file systems(In order of recommendation):-
Ext3
JFS
ResierFS
Ext2
XFS

Be careful during the partitioning part, if you choose the wrong partition then you could loose your important data.

---

### Post by luisfcup on 2007-11-27
I am confused
Shouldn't the bootable partitions be primary and not logical so the system can boot from them?
Who do you have WinXP in a logical drive?
Sorry if I am writing stupid questions.

---

