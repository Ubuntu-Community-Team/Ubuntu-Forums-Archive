---
title: "804ppc: Upgrade PB. Desktop ISO. Alternate. Useless"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by xerman on 2008-04-27
Hello there,

Last thursday, 2008.04.24, i did the distro update on the powerbook g4 17. Was using gutsy, and Update Manager notified the availability of 804 so I did the upgrade.

1- Upgrade process broke in middle of installation trying to upgrade OOO some latex filter was not available so the process did not continue and left system messed up. So

IT IS NOT SAFE TO UPGRADE POWERBOOK FROM GUTSY TO HARDY

I presume this has to do something with user configuration. My powerbook is in Spanish with SCIM on, and multilanguage support. ATI card...

2- After these issues i found my powerbook useless so I downloaded the 804 Desktop ISO PPC. USELESS. System will never start any kind of process. Placing the CD into the drive and starting from CD keeps the computer ON but with blank screen forever. I left the computer from Friday to Saturday (more than 24 h) and NO RESPONSE from system. Forced shutdown, and forced eject CD.

3- 804 Alternate ISO PPC does start the machine and is able to install the system, but I wanted to grow the New World partition, the bootable one and seems the CD is not capable of reformating this partition. And everytime i destroy the partition, create a new one, the system installs but after installation it will not boot. 
This because when i create a New World Boot Partition, Installation process tells that it is going to make bootable the partition, but KEEP DATA which is not possible in a recent created partition.
Now I have a complete system installed but useless due to the New World Partition being empty.

Any help regarding point 3 will be much appreciated. The issue to solve is:

- How to get a New World Partition reinstalled and up and running.

Thanks everyone.
Xermán

---

### Post by stream303 on 2008-04-27
Those upgrades have been problematic for some, without even using ppc.  It is kind of hit and miss depending on the situation.

If you are dedicating the whole drive to Ubuntu, I'd just start with the alternate disk again, and just let guided partitioning do it's thing without you having to do any deleting of existing partitions - it will overwrite them.

If you are dual-booting, use manual partitioning to delete all the old Ubuntu partitions, and the use the "go back" tab, and start guided partitioning again - this time using free space left from the deleted partitions.

I've found the go-back feature quite handy to delete old partitions, and then return to a guided-partitioning setup.

And, if your machine is using an ATI card, we are in newer territory with Hardy and xorg 7.3 quirks, so hang in there...

---

