---
title: "how to add a partition to an existing one"
date: 2010-08-17
forum: Apple Hardware Users
---

### Post by Colonel Dragoon on 2010-08-17
Hey, my question is quite simply this, how can I add a partition to an existing one, or add the space to the partition?
for example I am dual-booting ubuntu on my mac 5,5 on around a 7 GB partition, while mac was on the other 140gb, of course with extended use, these 7 gb quickly turned to 200mb of free space, which of course is severely affecting performance.

now the problem is that I reformatted my mac partition (hfs+) to (fat32) hoping that I'll just happily write on the mac partition while using ubuntu, which of course caused the loss of my mac data and my OS.
 anyway I've been using Ubuntu ever since, now what I wish to do is that I add the space of my original partition to the one I'm using in ubuntu, 
meaning I add the 140gb to the 7gb partition running Ubuntu, I deleted the mac partition causing it to be labeled as "Unallocated" in gParted, all I want to do is make use of the unused space in my partition.

now I'm sure if this is possible that there is a wiki or tutorial somewhere, but the thing is, I don't know what to search for, "adding partition" and similar searches only result tutorials on how to create a partition instead.

thanks

Screenshot description:

**/dev/sda2** : is a partition I made to install windows on to play Fallout 3...
**/dev/sda4** : is the Ubuntu Partition and the one I'm running now
**Unallocated** : is the partition or space that I want to add to **/dev/sda4**

---

### Post by atomizer on 2010-08-17
You can resize partitions with Gparted.

You must use a live-cd, because the ubuntu-partition has to be NOT mounted to work with it.

Backup your ubuntu data before resizing. 

It can take a while to resize the partition.

---

### Post by sxmjohn on 2010-08-17
Your not adding a partition all you need to do is format the unallocated section from the disk utility. Highlight the partition and and format to what ever file type u want.

---

### Post by Colonel Dragoon on 2010-08-17
> **sxmjohn said:**
> Your not adding a partition all you need to do is format the unallocated section from the disk utility. Highlight the partition and and format to what ever file type u want.
actually gParted won't let me format or unmount it or anything, the only options available for me are "new' and "properties"

> **atomizer said:**
> You can resize partitions with Gparted.

You must use a live-cd, because the ubuntu-partition has to be NOT mounted to work with it.

Backup your ubuntu data before resizing. 

It can take a while to resize the partition.
thanks, I'll try that as soon as possible, and if it hopefully works, I'll prefix to [solved] so that anyone can benefit from your answers

---

### Post by Colonel Dragoon on 2010-08-18
it didn't work, I backed up my data then ran my laptop through the live cd, I have the option to resize my partition since it's not mounted but I still can't do anything, with the unallocated partition I made, the only options I get for the unallocated 70gb are to check the properties. and I can only decrease the size of my ubuntu (exts4) partition, I can't really use the unallocated space to add to my current partition. it's basically just there without any options to do anything with it.

---

