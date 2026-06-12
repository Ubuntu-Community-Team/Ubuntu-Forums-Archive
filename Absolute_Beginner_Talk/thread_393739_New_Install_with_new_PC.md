---
title: "New Install with new PC"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-03-26
I have finally got my new super PC (64 bit AMD), so I need a guide as to the best way to install/partition/setup XP and Ubuntu.
 
I have a new 320Gb sata drive and I will put my older 80-Gb IDE Hdd in the new box. This smaller HDD currently has an ubuntu partition, a /home partition, and a swap partition. Current Edgy is 32 bit.
 
I want to end up with the abiilty to boot to XP. Edgy, and be able to install other distros as required (ed Fiesty and/or Sabayon), and have one /home partition and not upset the status quo.
 
Which way do I go please?
 
I am thinking;
 
XP and Edgy and /home on the large drive
Feisty on the smaller drive.
 
Can feisty/edgy then use the same home partition which contains all my personal data, emails, Firefox data etc?
 
I willupgarade to Feisty when it is realesed properly, Can i just install it and have it use my existing /home parition?
 
Lot's of questions eh!
 
Tony

---

### Post by indytim on 2007-03-26
Partition setup is a personal preference situation.  Here's what I did.  I have a 160G SATA and a 320G SATA.  The 160G is pretty much dedicated to my ops.  The 320 contains all of my files and one session of backups.  The alignment of my drives is

sda1 21G NTFS and boot - Windows 2000Pro
sda2 13G ext3 Kubuntu V6.10
sda3 Extended
sda4 20G Kubuntu 6.10 - Home
sda5 2.5G Swap
sda6 ext3 Xubuntu 6.10
remainder of 160 G HD unallocated for future ops and related

On the 320G HD:
sdb1 NTFS 20G Data for Windows 2k
sdb2 FAT32 40G Filesharing between Linux & Windows (data)
sdb3 Extended
sdb4 ext3 125G Media related files
unallocated 44G
sdb5 ext3 74G Linux backup

I intentionally left the unallocated on sdb where it is so I can grow either the sdb3 or sdb4 without much effort.

As I said at the beginning, the setup of partitions is a persona preference.  Hopefully the above will give you some ideas of how to proceed.

Good Luck,

IndyTim

---

### Post by tchoklat on 2007-03-26
thanks IndyTim! that is a good start.

Two questions. 

Can different versions on Linux all use the one /home partition or do I need one for each? I want to be able to reinstall and upgrade without affected my personal settings etc. I will install Edgy, but will want to upgrade to Feisty. Will my personal settings on /home be affected?


regards and thanks


Tchoklat

---

### Post by tchoklat on 2007-03-27
Need a helping hand.

Have new SATA drive
I will install XP on it, then 64 bit feisty as dual boot. If my original HDD with Edgy and /home partition is set as the second HDD,, can I use the existing /home partition with my data and settings on it for the feisty installation?


Tony

---

