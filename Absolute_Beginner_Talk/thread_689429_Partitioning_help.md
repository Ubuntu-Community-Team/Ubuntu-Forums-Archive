---
title: "Partitioning help"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Tek-Noir on 2008-02-06
When i installed gusty i did it on to a blank windows formated HD. During installation i chose to have 50% for ubuntu and left the rest. 

How would i go about making that all for ubuntu now?

Id like to just get rid of the partition and have the full HD for Gusty.

Cheers

---

### Post by Blue Sassley on 2008-02-06
There should be a option below the slider that says use whole drive.

Edited:

You could probably follow this too:

[https://help.ubuntu.com/community/HowtoPartition#head-a7b3b3837fbac5af4f996e6b68de9168781d78a1](https://help.ubuntu.com/community/HowtoPartition#head-a7b3b3837fbac5af4f996e6b68de9168781d78a1)


Blue

---

### Post by Tek-Noir on 2008-02-06
It wont let me move the slider at all

---

### Post by Blue Sassley on 2008-02-06
Hold on I'll reboot and take a screen of what I am talking about from the live CD.

Blue

---

### Post by Arwen on 2008-02-06
You can also use GParted([here]("http://gparted-livecd.tuxfamily.org/")) to manage your partitions and clean your drive,if ubuntu partitioner irritates you..

---

### Post by Tek-Noir on 2008-02-06
I can delete the windows partition and make a new linux one but would like to have it all one instead of having 2 separate ones.

---

### Post by forestpixie on 2008-02-06
if the ubuntu partition is after the empty space I believe it has to be moved to the beginning and then you resize to the right after the move
eg if the order is

sda1 - empty space
sda2 - buntu
sda4 - extended with swap inside

delete sda1, then move sda2 to the left, then resize sda2 to take up space remaining

---

### Post by Blue Sassley on 2008-02-06
Here look at this screen shot, you should have a second option below the Slider this says Guide - use entire disk

Blue

---

### Post by Tek-Noir on 2008-02-06
Would that no re install ubuntu though?

---

### Post by Tek-Noir on 2008-02-06
this is what im looking at.

---

### Post by dondad on 2008-02-06
> **Tek-Noir said:**
> It wont let me move the slider at all

You can't change the partitions while they are mounted. Boot from the live cd, load gparted and do it from there with the drive unmounted and you should be able to do what you want.

---

### Post by Blue Sassley on 2008-02-06
Yeah I'm sorry I missed read your first post... I would go with what Arwen said and boot on the Live CD then go under System ->> Partition Editor and delete the windows partition and then resize the Ubuntu partition to the whole disk. But if I were you I would go and get the Gparted Live CD over using the one on the Ubuntu Live CD because I have had issues with the one on the Ubuntu CD crashing.

Blue

---

### Post by Tek-Noir on 2008-02-08
Ah great, ill give that a go tomorrow, thanks for the help. Thought i might need to unmount the drive i was working on. lol

---

