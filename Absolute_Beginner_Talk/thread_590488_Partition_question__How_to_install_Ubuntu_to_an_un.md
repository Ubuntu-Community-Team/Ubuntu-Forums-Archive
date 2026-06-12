---
title: "Partition question?  How to install Ubuntu to an unpartitioned space?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2007-10-24
Hi,

I have a 120gb drive, 40 gb for XP, 55 gb for Vista & a blank partition of roughly 25gb for Ubuntu (I hope I didnt mess up on the math).  When I go to install 7.10 from the install CD, it asks about using all free space (not what I want).  I would like it to use the unpartitioned space.

How do I do that?

Thanks,
Rich

---

### Post by NoSmokingBandit on 2007-10-24
choose the last option "Manual." In there you can set it how you want? Im assuming this is your fist install. Choose the unpartitioned space and make an ext3 partition with all but about 500mb of the free space. Make sure its mount point is "/". Then take the 500mb you left over and make a swap partition. That should do it for you.

---

### Post by JoseArmandoJeronymo on 2007-10-24
You have to create some partitions for Ubuntu. Usually I make one for Ubuntu itself (that should appear as "file system"), another one for my files (that will be /home) and a small (300MB?) third one as a swap partition.

Just DON'T choose to use all partitions and Ubuntu installer will help you to create these partitions.

Try making the file system about 10GB. Home should be some 20 GB but you junst don't have that much space. And this brings me to another topic: my first Ubuntu box was a dual boot and I used more than half of my HD with Windows. After a while I was using Ubuntu exclusively and began to regret having left so much useful space to the other system.

---

### Post by RichTJ99 on 2007-10-24
So the swap should be be only 500mb?  Is more swap better?  Say a gig or two?

---

### Post by Maestro23 on 2007-10-24
> **RichTJ99 said:**
> So the swap should be be only 500mb?  Is more swap better?  Say a gig or two?

No.  If you have a good amount of RAM, you don't need a Gig of swap.

---

