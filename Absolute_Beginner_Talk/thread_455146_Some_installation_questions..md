---
title: "Some installation questions."
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Lebowski-Aus1 on 2007-05-26
Hello,

Now although i have been using Ubuntu for quite a while(Always Dual or Multi-Booting with XP, Vista) i have never really gotten my head around the whole partition setup options.

What i mean, is in the past i usually had the Windows partition a Ubuntu partition and a Swap, FAT32 drive for shared files. But i have read recently that its recommended to have a /home partition and i see i can make others like a /tmp partition.

So my question: If i plan to donate 50gb to Ubuntu all up, what size should the /Home partition be, and should i make partitions for any others like tmp, usr or anyothers..

My Partiton plan atm:  Windows Vista 80GB (For games only), 30GB FAT32, 50GB Ubuntu, 2GB Swap, 120GB Truecrypt partition.

Thanks in advance.

---

### Post by starcraft.man on 2007-05-26
The core files for Ubuntu, called the Root directory really only need 4 GB I think at base, I usually recommend 6 for buffer room so you can add lots of programs (I do >.>). A 2 GB swap is good. I give the rest of the 42 GB to the home partition, its really the data drive, the home partition stores all your local user/app config files as well as all media of that user.

That said, you can just increase your shared partition if all you want is more storage for Ubuntu (fat). I do recommend a home partition though, and you can't go wrong, maybe it will get ya spending more time in Ubuntu :D. 

You have to decide what you need. [This]("http://www.psychocats.net/ubuntu/separatehome") guide is good at explaining how to make a home partition after install. [This]("http://www.psychocats.net/ubuntu/partitioning") one discusses partitions in general. 

Hope that helps, adios :)

---

