---
title: "Hard Drive already partitioned?"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by Ninorcjw on 2006-11-06
I want to install Ubuntu and have a dual boot, my hard drive is already partitioned (from dell) into 2 drives, one is 80GB with windows on it, the other is 26GB with nothing on it. There are also  2 other partitions which i found through the disk management program, one is 47mb, "EISA configuration",  the other is 3.5GB with apparently nothing on it. I want to put Ubuntu on the 26GB part, im not sure if i should get rid of these partitions before i  install and partition it with the installer? Or something else? I'm completely new at Linux.

---

### Post by bigken on 2006-11-06
no leave them the small partion is the dell tools utiity and the 3.5 gig 
is a restore ghost partion for your windows os ;)

---

### Post by daxLeet on 2006-11-06
Mine was like this too.  I think the 26 [mine was 32] gb one is from Norton Ghost, which backs up all your files into that partition.  So I just deleted that and added an extended partition, with 2 logical partitions inside that [main + swap]

Make sure you have a ~1gb swap.

---

### Post by ReaderRat on 2006-11-06
Perhaps the easiest & safest way to go about partitioning is to use the -->> [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php) Live CD. Just download, burn, and use it.

---

### Post by Ninorcjw on 2006-11-06
Yeah i don't use the Norton Ghost, I do have a reinstallation CD,   so im thinking im going to get rid of that partition and partition it through the live CD when i install.

---

### Post by bigken on 2006-11-06
your 26gig partion I would use 8gig for your ubuntu system and twice your ram for swap ie 512mb = 1gig and the rest for a home partion 
this will have to be 3 partions created in a extended partion ;)


well if you have the restore cd get rid of the 26 gig and the 3.5 gig ;)

---

