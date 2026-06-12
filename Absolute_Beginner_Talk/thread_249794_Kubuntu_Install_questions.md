---
title: "Kubuntu Install questions"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Latintrans on 2006-09-03
Hi there: i ,am havin the next problms trying to install Kubuntu from live Cd, i can run the install wizard till the partitions section but there the problem is i can not identify which one is the C partition, i have 4 ntfs partitions in  my 40 GB hard disk  en  i am planing to use jus partition E, F, both of 10 GB to install Kubuntu, this is what i get after rezising the partitions 

my question is it possible that by accident i have some windows files are delete and then window should not start any more, because i understand the partitions to be use for the swap,home boot,user must format.

i hope it makes some sence this question, i am allready two days trying to install without succes

---

### Post by macdo on 2006-09-03
Windows and Linux have different ways of refering to partitions: Windows attributes a letter for each partition or Drive, with no distinction (A:\, C:\ D:\ etc). Linux is a bit more complicated than that, but gives you a lot more info. The drive gets a letter, and the partition gets a number. So imagine a PC with 2 hard drives and two partitions on each hard drive. Windows would have 4 drives show up: C:\ D:\ E:\ F:\
Linux would recognize 2 drives, called hda and hdb (or sda and sdb if they were SATA drives), and on each drive, two partitions: hda1, hda2, hdb1, hdb2

To return to your specific problem: there are two ways of making sure that you don't erase your Windows. 
1) Check the file system: if it's NTFS, don't format it.
2) Remember the size of the partition.

May I suggest you reconsider the partitioning plan a bit. 
You currently have 2 windows partitions that you want to leave as-is. These take up 20G on your HD. Linux needs at least two partitions to function: swap and /.
But here's the thing. Swap should't be 10G at all. A general rule of thumb is to give yourself a swap partition that's twice the size of your RAM: 1G of swap for 512 meg of Ram, for example. 
And you can't have linux partitions that use NTFS. Use ext3 for the / partition! (swap, of course, has it's own file system). 
You don't need to make any other partitions at all. A lot of people, including me, prefer to have at least one other partition for /home (again, formated in ext), but it's not at all obligatory.

HTH

---

