---
title: "partitoning problem"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Foresthello on 2007-10-30
I have ubuntu 7.10 if it helps


Ok heres my problem I was trying to install xp a while ago and when it loads up and gives me the options to repair ect. there was 2 options i think i clicked the other one then repair, i dont rember it was a while ago and it would start loading up and then it says something like please check floppy drive A and i dont have a floppy drive. 

Then i reboot it and i click repair i get the same error it s something like it cant detect my harddrive what should i do i cant get to the create a new partiton part of the windows xp disk.

So should i create a new partition with that disk that comes with the harddrive when you get it that creates a new partition?

Sorry i dont make much sence.

Thanks for the help in advance

---

### Post by mikewhatever on 2007-10-30
You really do not make much sense. At present, what are you trying to do? Are you installing Ubuntu or XP? What is the disk you got with the hard drive?

---

### Post by mdpalow on 2007-10-30
I have to agree with Mikewhatever; you don't make any sense. :)

However, I'll throw this at you and hope it fixes your problem.

If you have the Ubuntu 7.10 disk, put it in the drive and have your computer BOOT to CD.

After Ubuntu Live CD comes up, double click on the INSTALL icon on the desktop.

Answer some very basic questions and then when you get to the partition part, let it partition the entire disk.

It would be better if you did a MANUAL partition at this point and delete all partitions you might find and then create 3 partitions from scratch.

Might consider the following partition options:

1st:   /            EXT 3 file system     10 gigs
2nd:  /home    EXT 3 file system     The remaining left over except for 3 gigs
3rd:  /swap     3 gigs

Be sure to put a check mark in each of the small square boxes you see next to the partitions, so the get formatted as well.

Hope it helps.

If not, you might want to post a more specific question with some details as well.

Good Luck,

---

### Post by amtnbiker16 on 2007-10-30
sounds like you want to dual boot

i would completely re-format and start over.  install windows first, then linux
less problems this way

for some reason linux cant touch my windows partitions so shirink the windows volume using windows disk managemant before you install linux.  this will give you room for you to create new linux partitions

sorry if i went overboard and told you stuff you already knew

---

