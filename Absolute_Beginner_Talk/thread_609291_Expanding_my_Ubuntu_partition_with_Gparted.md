---
title: "Expanding my Ubuntu partition with Gparted"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by employeeno5 on 2007-11-10
Hi,

When setting-up Ubuntu I gave it a quite a bit more swap drive space than needed (11GB) because I was not yet sure what a swap drive was and I had an unused 11GB partition already on my disk. I've since used Gparted to reduce my swap down to just 2GB. I would like to take the remaining 9GB and apply them right onto my Ubuntu filesystem partition. 

Is this something I can/should do in Ubuntu? Will resizing the partition I'm using at the moment work, or potentially cause problems? 

Looking for any advice on the best way to do this. 

Thanks!

---

### Post by oilchangeguy on 2007-11-10
resize your swap/virtual ram to NO more than 512mb.

---

### Post by bluepowder7 on 2007-11-10
assuming that this new 9gig spot is right after your ubuntu (main) partition, you should be able to just delete that 9gig spot (make it unallocated), and then stretch the ubunto partition to that it reaches right to the swap space.  basically, extend the main partition.

i think that resizing to make bigger is generally safe with most file systems.  the shrinking can be problematic.

---

### Post by bulldog on 2007-11-10
You should use the Gparted live cd to do this kind of stuff.
But it all depends where the 9GB is located on your hdd.
If it is in a logical partition you can't give it to a primary partition if that is what you would do.


[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by employeeno5 on 2007-11-10
Thanks everyone! I should be good.

---

### Post by shad0w_walker on 2007-11-10
Your best bet is to ignore oilchangeguy. He is neglecting the fact that hibernation uses the swap partition to store your system state. Keep it atleast the size of your RAM if you want to hibernate, maybe a little bigger.

Anyway, if you are messing with your root partition (Where ubuntu is installed then you will want to use either the Gparted liveCD or the LiveCD of Ubuntu (Assuming you didn't use the text based installer) and run Gparted from there. It should be pretty easy to move and resize your partitions as needed. Good luck.

---

### Post by oilchangeguy on 2007-11-10
> **shad0w_walker said:**
> Your best bet is to ignore oilchangeguy. He is neglecting the fact that hibernation uses the swap partition to store your system state. Keep it atleast the size of your RAM if you want to hibernate, maybe a little bigger.

Anyway, if you are messing with your root partition (Where ubuntu is installed then you will want to use either the Gparted liveCD or the LiveCD of Ubuntu (Assuming you didn't use the text based installer) and run Gparted from there. It should be pretty easy to move and resize your partitions as needed. Good luck.

here's a thought, instead of all of the manual partitioning everybody seems to be so fond of, just let ubuntu set up it's own partitions. then the chances of f/ing up the operating system are greatly reduced.

---

### Post by bulldog on 2007-11-10
> **oilchangeguy said:**
> here's a thought, instead of all of the manual partitioning everybody seems to be so fond of, just let ubuntu set up it's own partitions. then the chances of f/ing up the operating system are greatly reduced.

I have to disagree with you.
It will only make two partitions,one for root and one for swap **you don't get a /home** 
And a /home or even a /data is essential if you have to reinstall so you have not to backup all your data.

---

### Post by oilchangeguy on 2007-11-10
> **bulldog said:**
> I have to disagree with you.
It will only make two partitions,one for root and one for swap **you don't get a /home** 
And a /home or even a /data is essential if you have to reinstall so you have not to backup all your data.

ok, but you still have to be intelligent enough to make a copy of the home file BEFORE a problem occurs.

---

### Post by shad0w_walker on 2007-11-10
Incase you missed it. He didn't break the OS. Just thought I would get that out of the way before anything else.

He presumably had some reason for manually partitioning his system. Perhaps he setup a separate home partition for instance or the Ubuntu partitioner wasn't giving him an option that matched his needs.

Now, how about you start being helpful or just leave him alone. People keep saying Linux users have an elitist reputation and I think you might just be a perfect example of that.

---

