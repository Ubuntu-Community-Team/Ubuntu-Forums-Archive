---
title: "Mounting Points"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Buttink on 2008-03-18
Ok. Well, im trying to install xp and ubuntu on the game hard drive. I have 4 partitions as of right now each basically the same size (125, they total to 500). So, basically i have this

media\sda1     Partition 1: Windows XP
media\sda2     Partition 2: Storage
media\sda3     Partition 3: Storage
media\sda4     Partition 4: Storage

What im trying to do is delete Partition 4 and install ubuntu on it. I dont know if this is possible but im trying lol. But, every time i try to manually try to edit partitions it says that i have "no root system". I know i can just set the mounting point to "/". But, i cant find anything that tells me what that would do. Anyway, i want to know what this actually does to my xp install. So would this actualy work?

media\sda1     Partition 1: Windows XP
media\sda2     Partition 2: Storage
media\sda3     Partition 3: Storage
/                      Partition 4: Ubuntu
                       Partition 5: Swap

???

---

### Post by Papa-san on 2008-03-18
media\sda1 Partition 1: Windows XP
media\sda2 Partition 2: Storage
media\sda3 Partition 3: Storage
/ Partition 4: Ubuntu ext3 (use 8 gigs for this 'root' partition, it's a generous amount, but you won't short yourself with it. You can go to 10, but don't really need to)
Swap Partition 5: swap or ext2 (this should be twice the amount of RAM you have 2 gigs ram= 4gigs swap)
/home partition6: ext3 (use the rest here)

You will do this partitioning during your installation.

What are you installing, and how? (live CD or alternate CD.)

---

### Post by Buttink on 2008-03-18
Thx! havent tried yet, but im about to. Also, Im useing the Live CD. I have installed ubuntu before, but i always just put it on a 2nd hard drive :). I didnt get that on this machine.

Wait...Im nearly positive its the live cd. The live cd i can start up ubuntu from the cd right?

---

### Post by dsauxier on 2008-03-18
Note that you can only have 4 primary partitions OR you can have 3 primary + several logical partitions.
Be sure when you recreate that 4th partition to tell it to be a logical partition.

---

