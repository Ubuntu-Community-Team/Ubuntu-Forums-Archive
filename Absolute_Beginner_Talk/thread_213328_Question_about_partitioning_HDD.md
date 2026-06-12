---
title: "Question about partitioning HDD"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Fridericus on 2006-07-11
Hello.

This is my situation. I have a 80GB HDD, its not split up to any partitions so Windows is currently using all of it. About 30GB is free space.

I was thinking of installing Ubuntu again (I had to desert it when it became incompatible with my GPU), however I dont want to re-install Windows again to set it up in the way I wish to have it.

So to my question, is it possible for Ubuntu during the installation to create a new partition without having to re-format the whole HDD and thus losing the Win XP installation?

I was thinking of having it set up like this.
Ubuntu - 10GB or 15GB
Shared partition FAT32 - 10GB
Swap - 1GB
the rest - the already installed Win XP

Is this possible without destroying the already installed data?
I always thought this wasn’t possible. :-k

---

### Post by Kobalt on 2006-07-11
Yes it's all possible... First you need to defragment your drive (so that you don't lose any data). Then get a Live CD of Ubuntu, start your computer with it, and start GParted : the partition tool. It will allow you to resize your windows partition, create a new shared one, and one for Ubuntu. You don't need to create the swap one, just indicate the partition you want to give to Ubuntu and the installer will make the right swap partition (size and place...) for your system. The space you want to allocate to each system seems fine, though Ubuntu system and apps won't need 10 or 12 Go... Or maybe you have super heavy apps !

Cheers !

---

### Post by Fridericus on 2006-07-11
> **Kobalt said:**
> Yes it's all possible... First you need to defragment your drive (so that you don't lose any data). Then get a Live CD of Ubuntu, start your computer with it, and start GParted : the partition tool. It will allow you to resize your windows partition, create a new shared one, and one for Ubuntu. You don't need to create the swap one, just indicate the partition you want to give to Ubuntu and the installer will make the right swap partition (size and place...) for your system. The space you want to allocate to each system seems fine, though Ubuntu system and apps won't need 10 or 12 Go... Or maybe you have super heavy apps !

Cheers !

Thanks Kobalt. 
I'll get right on it. :)

---

### Post by Kobalt on 2006-07-11
> **Fridericus said:**
> Thanks Kobalt. 
I'll get right on it. :)

You're more than welcome, let us know how your installation goes.

---

### Post by Fridericus on 2006-07-11
Still de-fraging. :)

50% complete, I got a question though. Will the spaces between the data be a problem once I start making the partitions?

[IMG]http://web.telia.com/~u48019550/defrag.jpg[/IMG]
I had a few things wrong, the free space is 41GB. :mrgreen:

---

### Post by kripkenstein on 2006-07-11
First - do a backup! Any partitioning of a HD should be done only after important data is backed up.

Second, regarding your last question: you can only resize your Windows partition by making it shorter, i.e. taking space from the end (taking from the start and moving it isn't a good idea). So the space left at the end is all you will have to work with. Looks (visual guess here) like you'll have about 15-20GB free, so that should be enough for Ubuntu.

---

