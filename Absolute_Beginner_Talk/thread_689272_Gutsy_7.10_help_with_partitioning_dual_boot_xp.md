---
title: "Gutsy 7.10 help with partitioning dual boot xp"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by DeltaUK on 2008-02-06
i have windows xp running fine right now, i have had to format my drive so many times recently because of linux so this time i dont want to screw it up.

i am using a guide from another site, seems simple enough, but the guide only shows me how to install using the auto resize partition option.

this is fine but my problem is i only want to use 30gb for linux, and i have a 750gb hdd.

the option gives u a slider of how big u want the linux partition to be, and the smallest partition it would make was 300gb! i had the slider fully to the left.. if i put the slider fully the right it showed the partition was going to be 700gb, so wait, i am confused about what this slider is showing.

is the slider how big the linux partition will be, or how big the windows partition will be after resizing?

* i have used 300gb in wondows *

:confused:

---

### Post by Algus on 2008-02-06
The slider is for determining how much space you are going to use for your Linux partition.  So say you have a 40 GB drive and you put the slider down to 8 GB, it'll shrink your partition to 8 GB and then use 32 GB for Linux 

You can download gparter, which works from a liveCD.  It's a pretty useful partitioner and helped me fix up my partitions after I goofed on my first Ubuntu install.

---

### Post by broekskw on 2008-02-06
morning algus, what program are you using to partition your h/drive, gparted is a great disc that will let you resize your h/drive, take a look at the links and see if they will help you

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
[http://gparted-livecd.tuxfamily.org/larry/livecd/livecd.htm](http://gparted-livecd.tuxfamily.org/larry/livecd/livecd.htm)


also see if this video helps, sorry can not updoade, if i find the site that has  the video guide will post for you:lolflag:

---

### Post by bumanie on 2008-02-06
Either use gparted live cd or when up to the partitioning stage during install, choose the manual partition option. Be aware (if you don't already know) that linux needs a / and a swap partition. The swap partition is like virtual ram - if your ram is fully utilised, swap will be used. It should be 1-2x the amount of your physical ram.

---

### Post by bwtranch on 2008-02-06
I like fdisk. No frills and it's CLI.

---

### Post by DeltaUK on 2008-02-06
so the slider isnt actually how big the linux partition is going to be.. its how big ur current partition will end up as. 

how confusing

---

### Post by dstew on 2008-02-06
I don't like the slider. I think it is better to use manual and enter the numbers in the boxes.

---

### Post by DeltaUK on 2008-02-06
im worried to use manual, it says select partition, there are 2, one is ntfs (windows) and the other is only 8mb
so i have to select my windows partition, then do i go to edit partition and make it smaller?

---

### Post by djnet on 2008-02-06
I dont much like the slider either...i dont much care for live cd all together...lol

---

### Post by dstew on 2008-02-06
> so i have to select my windows partition, then do i go to edit partition and make it smaller?Yes, if you want to make room for an Ubuntu installation on that drive. You need to shrink the Windows partition. I am assuming that you have no unallocated space.

---

### Post by DeltaUK on 2008-02-06
i have no unallocated space.

shrinking the windows partition wont currupt windows will it?

---

### Post by sandysandy on 2008-02-06
> **DeltaUK said:**
> i have no unallocated space.

shrinking the windows partition wont currupt windows will it?

as a normal practice u should backup important data before resizing. 
i have used gparted to resize windows NTFS partition with no problem.

regards

---

### Post by dstew on 2008-02-06
> shrinking the windows partition wont currupt windows will it?There is no guarantee. Back up first. Defragment the partition from within Windows. Once the shrinking process starts, it might take a long time. With that big partition, it could take as long as defragmenting (an hour or more). Do not interrupt the shrinking process while it is going on. But, if your power goes out, you could lose the partition. That is why backing up is important.

All that being said, I have installed on 4 machines, shrinking partitions 3 times, and had no problem.

---

### Post by DeltaUK on 2008-02-06
how do i backup windows? i dont see any obvious way.. i have 300gb used in windows that i dont want to lose.

---

### Post by ubutufan on 2008-02-06
Backing up windows or any other operating system is a different process than backing up data.
Therefore you want to use software on the likes of CLONEZILLA or anything similar to take a full copy of your windows and the data. You would need to have to disks to do that, the second one with good enough capacity to be filled in with windows operating system and data.

I do agree that resizing your partitions comes with absolutely no guaranty. But for whatever is worth, I have resized partitions using the GPARTED livecd 100+ times with no failures. Non whatsoever.

---

### Post by dstew on 2008-02-06
What I am referring to when I say backup is save your data, and have a plan for restoring your Windows operating system if you have to. That is, copy your data files (pictures, documents etc.) to some safe place, and have a Windows install CD at hand. To make a full clone, you need to do something special, like ubutufan recommends with clonezilla.

---

### Post by ubutufan on 2008-02-06
> **dstew said:**
> What I am referring to when I say backup is save your data, and have a plan for restoring your Windows operating system if you have to. That is, copy your data files (pictures, documents etc.) to some safe place, and have a Windows install CD at hand. To make a full clone, you need to do something special, like ubutufan recommends with clonezilla.

I fully agree with dstew. If you are not certain or familiar with this kind of operations don't do it.

---

