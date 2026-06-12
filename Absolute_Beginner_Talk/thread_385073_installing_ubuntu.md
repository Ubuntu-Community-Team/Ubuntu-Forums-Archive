---
title: "installing ubuntu"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by MONKEY4SALE on 2007-03-15
well i finally got ubuntu working on a CD but now i want to install it on my computer, durign the install process it asks if i want to erase my entire harddrive or set up my own partition, so since i dont want to erase my harddrive i need to set up my own partitions right?

---

### Post by lamalex on 2007-03-15
yes use the manual partioner. its very easy to use if you understand partioning.

---

### Post by glenndavy on 2007-03-15
right

do you have space on your hard drive for another partition, or is it full taken up with windows (or other) os?

---

### Post by Kobalt on 2007-03-15
Exactly. If you need any help, I suggest you read that step by step with screeshots guide : [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Welcome, to the real world ;)

---

### Post by mi_were on 2007-03-15
> **MONKEY4SALE said:**
> well i finally got ubuntu working on a CD but now i want to install it on my computer, durign the install process it asks if i want to erase my entire harddrive or set up my own partition, so since i dont want to erase my harddrive i need to set up my own partitions right?

A good place to start would be to check under your windows OS if u have about 4 GB free. That will leave you with atleast 1GB to continue using windows (just) and 3 GB to  get a decent installation of Ubuntu.

If u have enough space then FIRST backup everything on you computer (I didn't and lost everything while partitioning rare thing but it happens) then partition away and start Ubuntu-ing

---

### Post by jimbren on 2007-03-15
Before you try to do manual partitioning, make sure you defragment the hard drive from within Windows.  Windows writes data all over the drive regardless of how much space is available, and if you don't partition, you can lose data and make Windows inoperable in some cases.  

As Kobalt mentioned, [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) is an excellent resource for getting help with installation and configuration.

jimbo

---

### Post by MONKEY4SALE on 2007-03-15
alright i have 16 gigs, free

i'll defragment(it will take allllll dayyyyy) and then take 5 gigs away during the ubuntu install and put it into an extended partition, correct?

---

### Post by glenndavy on 2007-03-15
so here's a stupid question for everyone else... if he's got 16 gb free, I assume that means in his ntfs partition, not after it.. how will he make a linux partition? will the current installer/partitioner provide facilty to shrink that existing ntfs partion and file system?

---

### Post by Kobalt on 2007-03-15
Yes, GParted can do that.

---

### Post by glenndavy on 2007-03-15
> **Kobalt said:**
> Yes, GParted can do that.
nice

---

### Post by MONKEY4SALE on 2007-03-15
so i do create an extended partition and then put the 2 gigs for operating and left over for memory? how do i designate which one does what?

also, does it matter if when i go to look at my partitions i have no unused ones?

and how do i backup my harddrive in a way that im sure the partition wont get rid of it too? i dont have an external harddrive....

---

### Post by MONKEY4SALE on 2007-03-16
Also, on  another forum, i was told that i needed to have free partitions on my harddrive for this to work, 

but doing the partitions maneully makes those partitions, correct? and i already have 3 partitions on my computer and it says i can only have 4 at one time, so i need to make an extentded partition with logical partitions inside, right?
[IMG]http://i9.photobucket.com/albums/a90/monkey4sale/Screenshot.png[/IMG]
i seem to be incapable of partitioning my harddrive, it cant resize the drive for some reason

---

### Post by dstew on 2007-03-16
Did you defragment the drive just before starting the partitioning process? If there is even one sector being used in the part you want to free up, gparted won't let you shrink it. Otherwise, your partition plan seems to be fine.

---

