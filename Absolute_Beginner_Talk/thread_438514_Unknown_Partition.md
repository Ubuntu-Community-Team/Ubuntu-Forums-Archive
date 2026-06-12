---
title: "Unknown Partition?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by river16 on 2007-05-09
Hello, I am partitioning my hd in preperation for installing ubuntu dual boot with win. xp.
 I already have 3 partitions: one for windows, one restoration partition, and a third mystery 
partition that is 1gb ntfs.

Now I resized my windows partition and made a new one for linux, I want to add a swap partition for linux, but it says that I can not have more than 4 primary partitions. Does anyone know what is possibly on the 1gb partition? Is there any way to have more than 4 partitions?

Thanks (I am knida noob, sorry)

---

### Post by alienexplorers on 2007-05-09
You have to make an extended partition.  Then you can add the other partitions within the extended area you created.

---

### Post by taurus on 2007-05-09
Yes, you can have more than 4 partitions.  However, you cannot have more than 4 primary partitions.  You need to convert one of the primaries into extended partition and then create many logical partitions under that extended partitions.  

That's how you get around the 4 partitions limit.

---

### Post by PILGU on 2007-05-09
You cannot make more than 4 primary partitions. In Windows check with disk management  to see if there is any data in it. if not you can delete it and reuse it. you will be able to use part of it as swap and the rest atach to one of the other partions. By default windows creats one big primary partition that is Drive "C".

---

### Post by river16 on 2007-05-09
So let me see if I understand it: I make a new partition that is basically a "part" of the linux one. How do I do this?

---

### Post by river16 on 2007-05-09
oh, yah, I am using gparted to partition if that helps.  I found out that you can only have 1 extended partition, or something like that, anyway one of the partitions is ext3 is that it?

Thanks

---

### Post by alienexplorers on 2007-05-09
Delete you last partition.  Use gparted to make and extended partition out of that space.  Now select that space and select make logical partition.  You don't have to use all the space with one partition.  You can make several logical partitions within the extended partition.

---

### Post by river16 on 2007-05-09
Got it, now I am wanting to make a partition to add all the files to be used by xp and ubuntu, should this be a logical partition under the linux extended, or should it be a primary.

Also, about that 1 gb should I just delete it, is there any danger to my xp system if I do?

---

### Post by river16 on 2007-05-09
will i be able to access a logical partition under linux in xp?

---

### Post by PILGU on 2007-05-10
from Linux you will be able to see the XP file/folders but to see linux fromXP you will have to use "True Crypt", an open source program.  [http://www.truecrypt.org/](http://www.truecrypt.org/). If I where you and the 1GB partion has no data in it I would do as I told you before. if there is data, move it to the XP partion and do the same. It,s best to have a ROOT &Home partions for UBuntu so that if you where to mess up the OS and have to reinstall ubuntu your saved files and folders will remain intact. use Gparted on the Live cd to partion.

---

