---
title: "User swap"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-01
What is it?
Can I change the size of it? 
I have 2GB of RAM. Can it be swaped over the ram. (I rarely use 512MB of RAM)
At what point will it be used (As its never been used before, of that I've seen)


Thanks

---

### Post by Rolcol on 2008-03-01
It's used when you have insufficent RAM.

---

### Post by scragar on 2008-03-01
swap will normaly only be used if your programs are using more than the ram available, however I have had instances where programs that are zombified and such get stored in swap to allow for more cacheing(spelling?).

you should be able to resize your swap partition fairly easily using the Gparted program.
```
sudo apt-get install gparted
```

---

### Post by Tom--d on 2008-03-01
> **scragar said:**
> swap will normaly only be used if your programs are using more than the ram available, however I have had instances where programs that are zombified and such get stored in swap to allow for more cacheing(spelling?).

you should be able to resize your swap partition fairly easily using the Gparted program.
```
sudo apt-get install gparted
```

Installed that.
It doesn't allow me to edit it. 

How do you uninstall it?

---

### Post by scragar on 2008-03-01
```
sudo apt-get remove gparted
```
will work, however just incase it has a config file and your concerned about space use
```
sudo apt-get purge gparted
```

---

### Post by Tom--d on 2008-03-01
Thanks,

Is there any other way of editing the user swap?

---

### Post by scragar on 2008-03-01
I just tried it, you can edit the swap partition

launch Gparted(or Partition Editor as the menu calls it) and right click the swap partition, then choose "swapoff", do your changes, then "swapon" it to get your swap partition back with any changes you have done.

**WARNING:** don't do this if your short on ram at the time, who knows what negative effects removing swap when in use could have.

---

### Post by Tom--d on 2008-03-01
Ah, changed the size of it. 

What can I do with the left over? can I make it join my other partition?

---

### Post by Oldsoldier2003 on 2008-03-01
> **Tom--d said:**
> Thanks,

Is there any other way of editing the user swap?

You have to use a live cd to edit your swap partition- you can't edit a mounted partition

---

### Post by scragar on 2008-03-01
as Oldsoldier2003 said, you can't edit an inuse partition, so you can assign it to a partition not in use, but not partitions current mounted unless you use a live CD or something similar.

---

