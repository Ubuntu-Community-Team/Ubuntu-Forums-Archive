---
title: "Can I mount one drive inside another?"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Twizzle on 2008-01-19
I have two drives on my Ubuntu machine that I am using as a server. I have set one of the drives to ext3 after advice from everyone, and have it mounted under '/server/media' and shared so my media PC  and office PC can both access the drive (they are both XP machines).

As there is alot of space still on the install drive in the Ubuntu box, is it possible to partition the drive but have the new partition mounted as a folder inside '/server/media'? (Or even just have another folder instead of the partition?)

For example, I have /server/media/videos and now want /server/media/music, where /music is actually on a different partition.

I hope that make sense!

---

### Post by amo-ej1 on 2008-01-19
Sure that's possible. Every folder (no matter where it's located) is a potential mount location. It's even possible to have the same partition mounted at several locations.

---

### Post by Twizzle on 2008-01-19
Cool :)

In that case, is it best to partition the drive and add the new partition as a new mount into /server/media, or can I just create a new folder on the existing drive and mount that into /server/media?

I am guessing that the new partition route is going to be best but I like the flexibility of the folder option as it means that there is less restriction on the size. 

If I do go down the route of partitioning off a section - how much should I leave on the install drive for programs etc (I only plan to use the box as a server really)

(If it helps / matters my drives are hda - 150gb and hdb 230gb)

---

