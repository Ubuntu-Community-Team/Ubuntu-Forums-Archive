---
title: "Can't increase root partition size"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by InTeRnaTioNaL_BeGGaR on 2008-03-04
Hi I'm new to Linux and have started using Ubuntu 7.10 in my Dell Inspiron laptop.

My 80GB hard disk is divided into 6 partitions.

hda 1 is a hidden partition common in most dell laptops.
hda 2 is windows xp
hda 3 is linux
hda 4 is linux-swap and
hda 5 & 6 are other regular paritions.

Using the Gparted live CD, I took about 15 GB of space from the windows partition and made it free. So now the unallocated 15 GB space resides infront of the Linux partition and after the Windows partition.

However using the resize/move tool when I want to increase my root partition size it does not show the free space infront of the partition as space to be taken using the slider. However if I try to resize the windows partition it allows me to do that.

But what I need is to give this 15 GB of unallocated space to the root partition which resides AFTER the empty space.

Any suggestions?

---

### Post by zvacet on 2008-03-04
Download [Gparted live CD](http://gparted.sourceforge.net/),burn it on disc and boot with it.

---

### Post by Rocket2DMn on 2008-03-04
zvacet, he already said he used that :)
I think sometimes it just won't let you grow partitions, especially in front of itself (might be due to the location of the tables and whatnot for the filesystem).  It may also have to do with the fact that you must have some logical partitions in there.

---

### Post by cotcot on 2008-03-04
Is your root larger than 15 GB ?
Moving a partition that overlaps with its new location might be the problem.
In that case try to reduce its size to less than 15 GB and then move it and then enlarge it all with the theGparted liveCD. 
I think that the latest gparted livecd is able to move partitions with overlap.

---

### Post by mozetti on 2008-03-04
Haver you tried moving the linux partition first, so that it's immediately after hda2 and leaves the unallocated space *after* hda3? If that works, then you should be able to resize hda3 to use the unallocated space.

---

### Post by housam on 2008-03-04
zvacet is right . download the newer version of Gparted it'll allow you to do the front end resizing.
You can find it here [[COLOR="Red"]_http://gparted-livecd.tuxfamily.org/_[/COLOR]]("http://gparted-livecd.tuxfamily.org/")

---

### Post by hyper_ch on 2008-03-04
well, when you boot in a liveCD it will very likely mount the supported drives (at least the *buntu Desktop CDs do). This means before you can start resizing you have to unmount them.

---

### Post by InTeRnaTioNaL_BeGGaR on 2008-03-04
Thanks for the response guys. I believe I have the latest version of Gparted, coz I downloaded the iso like 3/4 days back. The root partition size was originally 3 GB to which I added another 1 GB from a spare partition which resided INFRONT of the root partition. That is why I'm a bit confused. I've already increased the partition infront once, but it's not letting me do it again. I already have checked about the mounting of the partitions and none of them are mounted.

> **mozetti said:**
> Haver you tried moving the linux partition first, so that it's immediately after hda2 and leaves the unallocated space *after* hda3? If that works, then you should be able to resize hda3 to use the unallocated space.

I was thinking about such a possibility, but how exactly do you move/swap two partitions (here the root and the unallocated space)....coz when I use the resize/move tool, the slider only shows me the area of the root partition, so a bit confused as how to "move" it.

---

### Post by bumanie on 2008-03-04
I haven't got the tool with me to test, however, form memory, when you want to move a partition there is a cross, whereas when you move the partition, there is a normal arrow. (Can't remember precisely, but I do remember that the cursor is different for the different operations). Have another look and notice the changes to the cursor when it is at the edge of the partition outline.

---

### Post by mozetti on 2008-03-04
> **InTeRnaTioNaL_BeGGaR said:**
> Thanks for the response guys. I believe I have the latest version of Gparted, coz I downloaded the iso like 3/4 days back. The root partition size was originally 3 GB to which I added another 1 GB from a spare partition which resided INFRONT of the root partition. That is why I'm a bit confused. I've already increased the partition infront once, but it's not letting me do it again. I already have checked about the mounting of the partitions and none of them are mounted.



I was thinking about such a possibility, but how exactly do you move/swap two partitions (here the root and the unallocated space)....coz when I use the resize/move tool, the slider only shows me the area of the root partition, so a bit confused as how to "move" it.

Ok, give us some more information. I see that you have 6 partitions listed, but there can only be 4 primary partitions on a disk. A little background:> There are 3 types of partitions:

_Primary_ - standard partition, use it any way you like (swap, root, home, data store, etc). There can only be 4 pirmary partitions on one physical hard drive.

_Extended_ - another type of **primary** partition, meaning it counts as one of your 4 maximum primary partitions that you can have on a disk. However, it's sole purpose is to act as a container for **logical** partitions (see below) to get around the limit of 4 primary partitions.

_Logical_ - works like a **primary** partition, meaning you can use it any way you like (swap, root, home, data store, etc), but it can only be created inside an **extended** partition.


So, you have obviously created an **extended** partition for your **logical** partitions to be created in because you have more than 4 partitions listed. I suspect that your **extended** partition was created immediately after the windows partition originally. 

So, when you resized your windows partition, the unallocated space is now between the end of the windows **primary** partition and the beginning of the **extended** partition. If that's the case, then that is why your resize tool won't allow you to move/resize the linux partition -- because it's inside the **extended** partition container and there is no room in front of the linux partition.

I'm trying to convey that you need to think of the **extended** partition as a container. So, you can't grow the linux partition because the space available is outside that container. You need to grow the container first, then grow the linux partition to use the newly available space.

So, if this is the case then you need to resize your **extended** partition to use up the now unallocated space between the end of the Windows partition and the beginning of the **extended** partition. I think you can resize extended partitions, but i can' remember.

Anyhow, once you do that then you should be able to move/resize the linux partition to use up that space.

---

### Post by InTeRnaTioNaL_BeGGaR on 2008-03-09
Hey thanx man. Yup it was the whole extended partition thing. Got what I wanted. Cheers.

---

