---
title: "Ubuntu on a seperate partition !"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by happyweb on 2006-08-19
i have a 80GB hard drive which has four partitions of 20 Gb each,
on C: i have windows 98 SE, F: drive is for backup and D: and E: drives are completely empty, now i want to install Ubuntu 6.06 on my pc and want to keep windows 98se as well , so by which option during the ubuntu installation will i be able to install ubuntu on my D: or E: drives and still keep windows 98 SE untouched..

---

### Post by steve.horsley on 2006-08-19
Pick either D or E and delete that partition. Don't just format it - delete the partition. Then in the installer, choose the option to use the free disk space. Ubuntu will create two partitions in that space - a main one for the system and a smallish swap partition for use as virtual memory.

---

### Post by frup on 2006-08-19
should be easy as... just place the ubuntu cd in the cd-rom and then when you get to the isntall process choose hda3 or 4 (or does it start from 0???)

the partition manager should let you see whether it is used or not too... you might have to click the advanced options just so you dont take over the whole drive

---

### Post by givré on 2006-08-19
> **frup said:**
> should be easy as... just place the ubuntu cd in the cd-rom and then when you get to the isntall process choose hda3 or 4 (or does it start from 0???)

Just to answer frup question ;) 
It's always start from 1, but the partition name could be different between from windows & linux, hda1 don't always mean that it's your C: partition.
But in the majority of the cause, if your HD isn't to much custom, that's right.

---

### Post by TripleE on 2006-08-19
Before you do the install when you boot the live CD.  Mount/open the partitions/drives and see what is on it.  Better to make sure you do not delete the wrong partition/drive:)

---

### Post by happyweb on 2006-08-19
> **steve.horsley said:**
> Pick either D or E and delete that partition. Don't just format it - delete the partition. Then in the installer, choose the option to use the free disk space. Ubuntu will create two partitions in that space - a main one for the system and a smallish swap partition for use as virtual memory.

is there any way by which i could install ubuntu without deleting any of my free partitions d: or e: (both are completely empty and FAT32 format )
and also still keep my windows 98SE untouched which is on c:

---

### Post by TripleE on 2006-08-19
I don't think so.  You will still need to create a linux swap partition (typically 1.5x the amount of ram on your system) along with a / (root) partition.  I would highly recommend deleting at least one of your partitions (d: or e: ) to install linux.  20gb is more than enough.  You can alway revert it back to an empty fat32 partition later if you like.

---

### Post by insane_alien on 2006-08-19
well, ubuntu needs to go somewhere. its either delete a free partition or delete a used partition. i know which one i'd do.

---

### Post by steve.horsley on 2006-08-19
> **happyweb said:**
> is there any way by which i could install ubuntu without deleting any of my free partitions d: or e: (both are completely empty and FAT32 format )
and also still keep my windows 98SE untouched which is on c:

No.

Linux cannot be installed in either FAT or NTFS partitions. If you tried, it would reformat to ext3. And you need a swap partition too. Like I said, delete one and tell the partitioner to use the free space. 

If you want to remove Ububtu later, you can always delete the Linux partitions and replace the empty FAT partition.

---

### Post by happyweb on 2006-08-19
> **steve.horsley said:**
> Pick either D or E and delete that partition. Don't just format it - delete the partition. Then in the installer, choose the option to use the free disk space. Ubuntu will create two partitions in that space - a main one for the system and a smallish swap partition for use as virtual memory.

as suggested i started my pc with a bootable cd and ran fdisk command ,after that i deleted one of my extended dos partitions    ( D: ) that was 20 GB in space and was completely empty , and then i shutdowned my pc and then restarted it and ran Ubuntu 6.06 and during installation steps when it reached the option to select hard drive space it is showing three options:
1) erase master hard drive etc..... (which i dont wanna do as i want to keep my windows 98 SE intact and untouched which is on my C:)
2) install in the largest continous free space.
3) make manual partition..

Now i selected the second option
and then it processed the step and then is showed me
that partition #3 will be formatted 
and  partition #7 will be used for swap purpose..

and then i got confused and aborted the installation

now was this second option correct and would this step had
installed ubuntu in D: (that was previously one of my partitions)

or do i hvae to follow some other steps in order to install ubuntu in the unallocated space (this unallocated space has been created when i deleted D: partition)

---

### Post by az on 2006-08-19
> **happyweb said:**
> 
and then i got confused and aborted the installation

If it helps at all, what the installer was saying sounds right.  You get one root partition (/) and one swap.


> **happyweb said:**
> 
now was this second option correct and would this step had
installed ubuntu in D: (that was previously one of my partitions)

or do i hvae to follow some other steps in order to install ubuntu in the unallocated space (this unallocated space has been created when i deleted D: partition)

You can tell if it using the free space by looking at the space it is telling you it will use.  You chose the right choice.

---

### Post by happyweb on 2006-08-20
Thanks you everyone for your prompt and informative sugestions
following which i managed to get ubuntu installed on my Box,
actually i took the option 2) which i talked a about and many of you also suggested to go for that option, it proved to be the right option as it installed ubuntu in the unallocated space which i had created my removing one of my partitions ( D: )

thanks again to all,
without all your support i would not have been able to 
install ubuntu on my pc

cheers 
happyweb

---

