---
title: "Visparted error, can't merge the unallocated space with hda5"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-03-14
I can't move the partition unallocated space to be merged with hda5, my ubuntu is located there.

I also received some error.

---

### Post by plucky on 2008-03-14
Select /dev/hda4 and resize the extended partition to take up the unallocated space,then move the swap partition to the end of the extended partition and then resize /dev/hda5.

Do not try this on mounted partitions and backup your data to be on the safe side.


Good Luck

---

### Post by karlo on 2008-03-15
> **plucky said:**
> Select /dev/hda4 and resize the extended partition to take up the unallocated space,then move the swap partition to the end of the extended partition and then resize /dev/hda5.

Do not try this on mounted partitions and backup your data to be on the safe side.


Good Luck

Sorry for the late reply. Is it something like this? :)

---

### Post by karlo on 2008-03-15
> **plucky said:**
> Select /dev/hda4 and resize the extended partition to take up the unallocated space,then move the swap partition to the end of the extended partition and then resize /dev/hda5.

Do not try this on mounted partitions and backup your data to be on the safe side.


Good Luck

IT HANGS!

What to do?

---

### Post by plucky on 2008-03-15
Never used visparted, Try Partition editor on Ubuntu live CD or download the latest gparted live CD and use that.

See [here](http://gparted.sourceforge.net/download.php=)

Good Luck

---

### Post by karlo on 2008-03-16
> **plucky said:**
> Never used visparted, Try Partition editor on Ubuntu live CD or download the latest gparted live CD and use that.

See [here](http://gparted.sourceforge.net/download.php=)

Good Luck

Why? I had used gParted and it's pretty boring. And I THINK it does not have a built-in browser, which will help you alot if you need some support while the VisParted Partitioner is working...

---

### Post by louieb on 2008-03-16
> **karlo said:**
> IT HANGS! What to do?
Give it time. Never used visparted - it  looks like GParted to me. but anyway GParted could take an hour or more to move the partitions around like you want to do.

---

### Post by karlo on 2008-03-22
> **louieb said:**
> Give it time. Never used visparted - it  looks like GParted to me. but anyway GParted could take an hour or more to move the partitions around like you want to do.

OK, thanks for that. Another question, do you know a site which shows some tutorials on how to use GParted or VisParted? Partition guides, understanding them etc...

---

