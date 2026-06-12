---
title: "New too this"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Redd Ryder on 2007-07-28
Hi......I have now downloaded the Ubuntu and copied on the CD.....used it all day today and love it....now I want to install it...however.....don't want to lose my XP either....this is a brand new gamer comp....I have 2  320G hd's....but I want to partition one of the drives.....as I use the other for storage......is this a good idea?   I have all my music and pics on my second one....plus I do have back-ups on Google.....is it better to leave Windows on e hd and use Linux on the second.....plus not quite understanding about the guided use whole disk thing....maybe I just need a little clarification

thank you in advance

---

### Post by moffa on 2007-07-28
Using one drive for linux and the other for windows sounds like a good idea.  Just make sure you select the correct hard drive during installation.  You could always unplug your WIndows hard drive during the installation, although you would have to install WIndows to the boot manager after (its pretty easy to do).

In any case, make a physical backup copy to cd/dvd just in case before you start having fun.

---

### Post by wolfen69 on 2007-07-28
like moffa says, just unplug the windows drive. you can always choose which drive to boot from in the bios. the guided use whole disk thing is what it says. it will use the whole drive for the ubuntu install. very easy.

---

### Post by Hobo Joe on 2007-07-28
It's easier to do with one hard drive, but that doesn't mean you still can't use two if you want to.

As far as the partitioning goes, it's pretty intimidating, but once you break it down, it's really easy.

1. While you're in the live CD, go to applications>administration>GParted. 

2. Select the hard drive, and resize the partition to the desired size, this all depends on your preferences

3. Select the space that has just been created via the resize, and create a new partition, formatted to ext3.

4. resize that to make about 2GB of free space.

5. In the 2GB of free space, make a partition, and format it to 'Linux Swap'

Alternatively, you can make a separate partition for your /home folder, which I would recommend. To do it, all you need to do is split the Ubuntu partition into two separate ones.

6. Then, when you install, select the ext3 partition as the root one, or if you have a separate /home folder, set one to /home, and the other to root. While you are doing this, make sure that the Windows partition(s) are NOT formatting.

Follow these instructions and you should be set.

---

### Post by Sef on 2007-07-28
> 5. In the 2GB of free space, make a partition, and format it to 'Linux Swap'

How much ram do you have?  Swap should be about double your ram, but if you have a gb of it or more then it becomes less important, unless you do heavy gaming, movie editing, or other graphic intensive applications.

---

### Post by Redd Ryder on 2007-07-28
> **Sef said:**
> How much ram do you have?  Swap should be about double your ram, but if you have a gb of it or more then it becomes less important, unless you do heavy gaming, movie editing, or other graphic intensive applications.

I have 3 Gigs of ram....

---

### Post by Sef on 2007-07-28
> I have 3 Gigs of ram....

I would not install a swap partition then.   It would be very unlikely you would ever need it.

---

### Post by Redd Ryder on 2007-07-29
thank you all for your input.....I think I might have made some small errors on my swap file and partitions......however...they are minor can be lived with......I do know that with your input....my duel boot works flawlessly and I'm loving it....but what is the difference between Ubuntu 16 generic and 15 generic....was curious.....and is there a website(s) where I can download programs for this OS

---

### Post by hyper_ch on 2007-07-29
Well, swap is needed if you want to hibernate your computer...

---

### Post by hyper_ch on 2007-07-29
well, those are just different Kernels... newer ones :)

For software, you should have in you applications menu somehere "Add/Remove" software...

Furthermore have a read here, this explains most basic things: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by nick.inspiron6400 on 2007-07-29
If you wanted to you could give Wine Windows Emulator a try? To get some of those games working!

---

