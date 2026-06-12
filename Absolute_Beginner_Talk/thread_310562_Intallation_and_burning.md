---
title: "Intallation and burning"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by up north on 2006-12-01
Yes I am a newnie. But from other software forums I know there is good support out there from the community.

I have searched the forums, but to no avail. I cannot get Ubuntu installed on my system. But I want to!!

Problem: Dual boot (hda ubuntu/hdb XP) 
protocol: found it here, so should work.

1 install was ok. After logging in 3 times I got a "tty" error. Ubuntu did not work. Re-istalling proofed not possible.

Burned the CD on work (42x and 4 x), cd checks out to be ok. At home CD = ok --> installation "irqpoll error" -->F6 "irqpoll" and "irqpoll route irq" both installations did not work. Checked CD --> "badcheckum" (WHAT!)

Burned the CD at home 6.10 and 6.10 (24x and 4c) always irq error, all CDs are bad. Just ordered 6.06 CD (but I want alternative CD so takes 10 weeks).

How can I get Ubuntu on my system.

System:

Athlon XP(1700+); K7T266 Pro2 (KT266A chipset)
758 MB memory; 
ATI raddeon 9550;
hda: Maxtor 60GB (master) IDE0
hdb; ST 160GB (slave) IDE0
CDwriter IDE2410 (master) IDE1

I do not know what else to list...

Anyway

How can I get a Ubuntu version 6.06 or 6.10 cleanly burned (CD brands, burning speed) and installed (do I need to check memory? Do I need to format hda first from windows?) WHat is the best way to partition the 60 GB disk?

I tried:
45 GB primary/beginning
15 GB secondary/end/fat32/mounted by windows
1.5 GB secondary/swap

I hope I listed everything please, please help me. 

Thank you already for reading this long :confused: mail

Marco

---

### Post by Pjotr123 on 2006-12-01
A possible source of errors might be the rather unusual master/slave construction for your hard disks. You could try the following:

- disconnect the empty hard disk (current master)
- change the Windows disk from slave into master
- create two extra partitions on the Windows disk (I assume you have spare space), using the Gparted LiveCD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
- install Ubuntu on the second partition and use the third as Linux swap.

Now you have a dual boot system with only one hard disk, which is the master.

Does this work? If so, you can reconnect the first hard disk, this time as slave, and use it only for data and not for operating systems.

Greeting, Pjotr.

---

### Post by up north on 2006-12-01
Nice fast reply. Thanks

I have a lot of data on the disk so will be difficult. 

I choose this setting because it was recommended by our IT suport of our university. I used to have hda (master) cd (slave) on IDE1 and hdb as master on IDE2 but then I got windows witing errors on hdb and was losing data when moving large file. 

But I am not an expert in this.... I have to investigate...

Other options`?

Marco

---

### Post by Pjotr123 on 2006-12-01
I am afraid that this might be crucial.

Perhaps you could format hda (current master) in FAT32 and move a lot of data from the Windows disk hdb (current slave) to hda.

Then you have the space you need on hdb, to follow the steps I described in my first post.

The ideal situation would be, to have the 160 Gb disk as master on it's own IDE cable, plugged into the first IDE slot on the main board (IDE 0). The smaller 60 Gb disk, formatted as FAT32 and containing only data, as slave on that same cable. 

The CD player also as master on it's own IDE cable, plugged into the second IDE slot on the main board (IDE 1).

Greeting, Pjotr.

---

### Post by up north on 2006-12-03
I am just a little lost how this is crucial. I have seen a nice tutorial on how to install a dual boot on two disks and that seemed to work.

My question is this: why did I get a tty error after 2 days of use, and why aren't any of the CD working on the installation when it worked in the first place?

Anybody else here agrees with Pjotr123 that I should try this first or should I try something else first?

Thanks

Marco

---

### Post by up north on 2006-12-17
Ok Now I installed the new upcoming Debian release and and that worked nicely. So was/is the previous Kernel of Ubuntu at all stable. And is there a new one?

So I installed Debian as I first Intended to install Ubuntu

Any feed-back?

Marco

(thanks)

---

### Post by up north on 2006-12-19
eh nobody care if I install Ubuntu at all? Is this ok software? Do you guys (who are users) at all concerned to get new users?

Marco

---

### Post by TooRight on 2006-12-19
Windows is a bully that wants to always be first and when it isn't, it starts throwing fits, lol, so yes, they DID answer your question. 

Defrag your windows drive well and then when you are doing your Ubuntu install, choose the option of guided install, then choose to have the partition program use the "install in the most free space" option. It'll set things up so windows is the first partition, Ubuntu is the second, with  the third being the swap partition. As for the empty drive (now the slave) make it a FAT32  so that both windows and ubuntu can access and use it for storage.

Also, when you're burning the cd, it seems like 4x is the speed with which people have the most luck.

Good luck!! :D

---

