---
title: "Install question"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Hantas on 2007-07-05
Hi,

I have a WinXP pc with 2 disks. 1 disk has 2 partitions (C and D), with windows installed on C and i have another disk that i use for my data with only 1 partition. 

Now i would like to install Ubuntu on my D partition, so that i end up with a dual boot machine (preferably with winXP as default OS). I started the installation process, but at step 4 i'm afraid to continue, because i don't want to screw stuff up. By the way, my D partition is empty (maybe some hidden/lost files left that i don't care about) and i don't mind formatting my D if that would be positive.

1) Can i install ubuntu on my D without screwing up my windows installation on C? (i assume so, but i'm just not sure about myself here)
2) How do i make sure that ubuntu is installed on my D partition? Please tell me what options to choose in installation step 4 (i'm assuming someone can just go check that so i don't need to type  my choices)
3) Assuming the installation works the way it should, would winXP (still) be my default OS?

---

### Post by lamalex on 2007-07-05
> **Hantas said:**
> 

1) Can i install ubuntu on my D without screwing up my windows installation on C? (i assume so, but i'm just not sure about myself here)
2) How do i make sure that ubuntu is installed on my D partition? Please tell me what options to choose in installation step 4 (i'm assuming someone can just go check that so i don't need to type  my choices)
3) Assuming the installation works the way it should, would winXP (still) be my default OS?

1) Yes, totally just watch your partitioning, install on /dev/hdb and don't even tough /hda.
2) pick /dev/hdb1 for your /(root) and /dev/hdb2 for <swap>
3) No, why would an os put itself not as default? that doesn't make any sense. You can set Ubuntu not to be default once you're in.

---

### Post by zek725 on 2007-07-05
> **Hantas said:**
> 1) Can i install ubuntu on my D without screwing up my windows installation on C? (i assume so, but i'm just not sure about myself here)
Yes.
> 2) How do i make sure that ubuntu is installed on my D partition? Please tell me what options to choose in installation step 4 (i'm assuming someone can just go check that so i don't need to type  my choices)
you can delete your D partition and have Ubuntu partition that free space.
> 3) Assuming the installation works the way it should, would winXP (still) be my default OS?
After a few configurations with GRUB, XP can be booted as your default OS.

---

### Post by Hantas on 2007-07-05
> **zek725 said:**
> 
you can delete your D partition and have Ubuntu partition that free space.


Ok, i deleted the D partition, so i now have a bunch of free space that i can create a new partition in. I should create 2 partitions there, right, one for swap and one for the os itself? So I guess they should both be a primary partition (not logical), one ext3 and one with swap?

How much should i use for my swap partition? I have about 150 Gb free now, so i don't really care about a few MB or even Gb more or less, but i have no idea how much it needs. I guess it doesn't matter where the swap partition ends up (beginning/end)?

---

### Post by zek725 on 2007-07-05
These links can help you in planning your partition: 
If installing with the desktop cd: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
If installing with the alternate cd: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

