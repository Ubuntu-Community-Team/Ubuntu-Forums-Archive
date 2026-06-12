---
title: "disk partitioning problem"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-09-27
hello xperts

when i installed ubuntu and it gave me the option to partition my drive space i manualy configured it thinking it would be similer to a windows partition program.(maybe it is but it didnt work that way for me.)

right, when it asked me to partition my space i took about 40gb of space and gave it ??? ext2 i think ???  
i let it then autoconfigure the left over space which it did by making another 40gb partition and a 2gb partition.
this gave me 2 partitions at 40gb and 1 partion at 2gb for swap space(virtual memory i think)
what it is is that you know how the first drive is labeled as / (root drive i think)
i thought i could label the second partition as /2 to give me a second file system in --- places/computer
the prob is instead of giving me a second file sytem, it gave the free space to a file called /2 inside of the first partition / (root)
i usually like to set my computer up as having (for example on a windows sytem)  c:\ for system files     d:\ for progs       e:\  downloads etc    
this is just an example to make you understand what im trying to do.

is it possible to get a second file system on the go in ubuntu?

if you cant be bothered to write an explanation for this then i would be v-happy at just being pointed to some info on it.
its hard to google a question like this i think.
the results i get are full of useless problem that have no relevence to my problem

---

### Post by Imsati on 2006-09-27
Depending on what you've done so far (as far as loading programs, moving files over, etc.) I would just re-load with different partitions.

For example, my Kubuntu drive has a 2 GB swap, 15 GB Root, and 40 GB Home directory (both formatted as ext2.

I manually partitioned everything, too--I like to know what is where.

---

### Post by uk_sphinx on 2006-09-27
i dont understand you

when you click on places....then computer
do you have 2 file systems?
do you understand what i have done?
i have a partition as a file in a seperate partition.

---

### Post by 789 on 2006-09-27
If I understand your predicament correctly this is what you need to do in partition manager:



partition 1 -- your wind FAT 32 or NTFS partition -- /dev/hda1
mount point /media/hda1

partition 2 -- your linux etx3 -- /dev/hda2
mount point /

and your swap partition at /swap


There might be a brand new installation in your immediate future

---

### Post by think13 on 2006-09-27
As far as I know, Linux does not have separate drive letters, it has one central drive, and what would be different drive letters in windows is just another folder in Linux.

What you are seeing is default Linux behavior.
Someone correct me if I'm wrong.

---

