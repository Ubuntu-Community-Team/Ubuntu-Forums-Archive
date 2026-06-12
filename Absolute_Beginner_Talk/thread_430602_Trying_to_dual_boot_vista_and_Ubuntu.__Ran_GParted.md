---
title: "Trying to dual boot vista and Ubuntu.  Ran GParted, now system won't boot into Vista"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by dmorand on 2007-05-02
I just bought a Presario V6000 laptop, and want to have it dual boot Vista (Preloaded) and Ubuntu.  I downloaded GParted so I could repartition my hard drive because the system was loaded with Vista containing the whole drive.  I partitioned it out as:

45 gig ext3 
1 gig Linux swap
88 Vista ntfs drive
6 gig compaq backup drive

I formatted the two linux partitions in Gparted, then rebooted to make sure I could boot into Vista.  I unfortunately can't boot into Vista now.  It loads, but then the system recovery loads and gives an error stating that the problem can't be fixed and Vista won't load.  

Is there something that I should have done in Gparted to ensure that Vista would be able to load properly?

---

### Post by jkblacker on 2007-05-02
Is that the exact order you partitioned your hdd in?

---

### Post by dmorand on 2007-05-02
The first thing I did was resize the partition because it was all partitioned to a ntfs drive.  I shrunk it down to 88 gigs.  Then I partitioned the ext3 partition, then the swap partion.  The last step I took was to format the ext and swap partitions.

---

### Post by dmorand on 2007-05-02
Actually now that I think of it, I think I have my two linux partitions defined before my vista partitions.  Does that really make a difference?

---

### Post by rusty4r on 2007-05-02
On my older compaq after altering the size of the windows partition the recovery partition didn't recognize it anymore and therefore was useless. My windows partiton was still there and I think yours probably is too your grub just didn't see it.

post the output of```
 fdisk -l
```
where the "l" is an ell not a one

and the contents of your menu.lst file. (Which is at /boot/grub/)

---

### Post by dmorand on 2007-05-02
where do I run fdisk -l ?  I only have Vista installed (which doesn't load).  Do I run that in Gparted somewhere?  Sorry, but this is my first experience with Gparted, and linux.....

---

### Post by jkblacker on 2007-05-02
I'm thinking if you put your linux partitions in front of your vista partitions you may have overwritten your vista data...

---

### Post by dmorand on 2007-05-02
Ok, that's not a big deal.  I haven't done anything on the vista yet, and I have my backup cd.  I will just reload the vista, then run Gparted, but this time I'll put the linux partitions after the vista partitions.  It still loads vista, it just goes into the system recovery to fix errors.  Maybe I can tinker with it to work right.....if not, back to the drawing board.

---

### Post by jkblacker on 2007-05-02
Yeah, I think that's probably the best bet! Also, I'm guessing why the advice is to defrag before partitioning on a used system (possibly even on a fresh install of both, not sure), to make sure all the important windows data is moved to the front of the disk?

---

### Post by dmorand on 2007-05-02
It takes forever to resize partitions, I guess I have another long night ahead of me......oh well, live and learn.  That's what I say!

---

### Post by floke on 2007-05-02
I've read - though don't know - that the gparted utility cannot resize a Vista partition without damaging it so that Vista won't load. From what I read there's a partition utility in Vista itself that you have to use first; and then use gparted to format the empty space you create.

---

### Post by dstew on 2007-05-02
You will probably need to re-install Vista to recover. After than, my advice is use the Vista Disk Management tool to shrink the Vista volume. It is in the My Computer --> Manage --> Storage --> Disk Management --> Shrink Volume. There have been issues using GParted to resize Vista NTFS partitions. Once the Vista partition is shrunk, you can use GParted to create new partitions from the unallocated space.

---

### Post by dmorand on 2007-05-02
Thanks Steve K and dstew!!  I didn't realize there was such a utility built into Vista.  I'll do that then run Gparted after to create the 2 new linux partitions.  Thanks!!!!

---

