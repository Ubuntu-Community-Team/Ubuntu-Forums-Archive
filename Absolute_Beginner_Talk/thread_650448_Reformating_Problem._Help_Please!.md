---
title: "Reformating Problem. Help Please!"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by KudoKid on 2007-12-26
I am trying to reformat my computer to windows XP, and later this week, will make it dual boot with Ubuntu.
However, this is my first time every reformating from a different OS to windows, and i've encountered an issue.
When i am given the choixe of which partition to install windows onto, I am given disks I and J, Now i usually get C and maybe D, but this is the first time i have ever gotten I or J.

Partition I is 235523 MB, which is like 230 gigs, (my hard drive size), but the I part confuses me. Is the reason for the name change because i swaped to Ubuntu? it was called file system so i never really thought about the name difference from local disk C to File system.

Please help. Many thanks.
Happy Holidays!
KudoKid

---

### Post by Cypher on 2007-12-26
Since you want to reformat everything, you're best off just pretending the HD is brand new and delete all the existing partitions..I believe that's the "D" option for each of the partitions..once every partition has been erased, it should say "unformated space" for the whoe 230 Gigs..

Now, create a partition for XP and it will show up as C, since you want to dual-boot later on, make this partition enough for XP and whatever application/usage you have for XP, leave the rest of the space unformated.

Finish the XP installation and later on when you go to install Ubuntu, create your /root, /home, /usr and SWAP partitions with the free space you have..

---

### Post by KudoKid on 2007-12-26
Okay, i'm about to erase the 2 partitions and do that, i'll let you know how it goes.

---

### Post by KudoKid on 2007-12-26
Terriblyy sorry for the double post, but i have changed my mind on something. I want to make it all windows partition, so would i just make that first partition the full amount? In other words, I am putting just windows on it (just for a while, don't worry. lol.)

I went ahead and made 1 partition. sorry for the confusion, seems to be working good so far. Thanks a ton! =D

---

### Post by Cypher on 2007-12-26
I see that you answered your own question..but yeah if you only want Windows on there you can create just one large partition.

I've historically created 2 partitions, a smaller one for Windows and system programs and another one for user programs and documents. Unlike Linux where keeping your /home seperate means that you can upgrade/install any new Linux without harming your files, this doesn't always work as smoothly in Windows..so in most cases, this just overkill..

---

