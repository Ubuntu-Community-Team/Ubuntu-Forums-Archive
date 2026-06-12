---
title: "How to go about creating your very own /home partition..."
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-07
How would I do this if I already have 5.10 installed in the default way (a "/" partition, and swap partition)
I would like to make my current /home directory its own partition, so i can put all of my settings and data in there before i upgrade to dapper.

---

### Post by garner_nc on 2006-05-07
You may be able to shrink your / partition using gparted to create enough free space to create another partition. If it was me, and I didn't have a lot of other pacakges installed, I would back-up my personal files and re-install creating a home partition.

As an alternative you could install another hard drive and create a /home partiton on it. Then you create a symbolic link to the new /home partiton in your / partition. I've done this on many machines with great success.

All the Best,
Doug White

---

### Post by user1397 on 2006-05-07
[quote=garner_nc]You may be able to shrink your / partition using gparted to create enough free space to create another partition. If it was me, and I didn't have a lot of other pacakges installed, I would back-up my personal files and re-install creating a home partition.

As an alternative you could install another hard drive and create a /home partiton on it. Then you create a symbolic link to the new /home partiton in your / partition. I've done this on many machines with great success.

All the Best,
Doug White[/quote]
Thanks for the suggestions I will try the re-install idea, as I don't like g-parted, and i don't have another hard drive!

---

### Post by nalmeth on 2006-05-07
you may prefer disk drake (pclinuxos livecd, click install to harddrive, do partitioning, then cancel install)
or qtparted (knoppix liveCD)

---

