---
title: "Kubuntu reinstall - Need to know some stuff"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-06-04
Hello,

I have 25GB to spare. So is it ok I have 1.5GB for swap and 20GB for root? 
What mount point should I select for the rest of the space? (Previously I selected /home, is that ok or should I select something else?)

Is it ok if I have the entire drive (excluding swap) to be root? I am afraid, I dont understand how this works. If someone could guide me through this partitioning task, it would be helpful. 

In windows, when you install any program, it normally gets installed in C:\Program Files. Is there a common folder like that in Kubuntu where all the software gets installed? 

Thanks,
SS

---

### Post by Inxsible on 2007-06-04
Check this link for more info on partitioning:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

and this one for installing:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by linuxnovice on 2007-06-04
I have seen both these links before. But they are not much help to me. Unlike most people here, I already have my machine partitioned when I installed XP. I have 25GB of unallocated space ready for linux alone. My concern is to how to use this space effectively. I saw some posts which told me that the root partition must be nice and big because thats where all the stuff is installed. But some other tell me that, root partition can be set to a minimum and I can have my /home as a seperate partition and make is huge. 

This is where everything is getting confusing for me. So which is the best and the ideal way to partition for linux? Since I have 25GB of unallocated space, I dont need to worry about resizing my windows partition for kubuntu. I will chose the manual partition method. Considering this, I would like to know the best way to go about partitioning it.

---

### Post by zvacet on 2007-06-04
1.root =10GB mountpoint /
2.swap==2xRAM 
3.home =rest of free space mountpoint /home

---

### Post by akudewan on 2007-06-04
IMO, partitioning is just a matter of convenience and organising stuff. There are also performance issues, but I don't think that home PCs have to care about that, since our hard-disks are not very large.

You can have one large partition for root, and the whole of linux, or you can separate your /home partition. The root partition must be big, but not necessarily very big. 15GB should be ok.

Personally, I prefer a large /home partition, because I have a lot of videos stored.

The swap size should be about 3 times the size of your RAM.

---

