---
title: "Help with installing on partiton on hard drive"
date: 2010-07-15
forum: Apple Hardware Users
---

### Post by flatlined on 2010-07-15
I want to install Ubuntu 10.04 PPC along side my mac OS  on a partition on the inter hard drive that I created with 10.5 disk utility. When I get to the part in the Ubuntu installer where it ask where to install I only see the whole hard drive and not the partition I made, and when I go into the partition menu I click on it there but it won't let me install it. Can someone walk me through how to put it on a partition on my hard drive or is there a step by step somewhere?

Thanks

---

### Post by flatlined on 2010-07-16
So what would I need to make each of these if I want to install Ubuntu onto a 15GB Partion and my Mac as 1GB of RAM:

/root
 /home
  swap
 /opt

Thanks

---

### Post by flatlined on 2010-07-22
Any help? Also I made another partition on my internal drive for 15GB if that helps.

Thanks

---

### Post by Nick_Jinn on 2010-07-22
Its easier than you think. Just plop in the disk and when it loads click on 'install'. The whole process is guided.

---

### Post by flatlined on 2010-07-22
> **Nick_Jinn said:**
> Its easier than you think. Just plop in the disk and when it loads click on 'install'. The whole process is guided.


Yes I've done it that way on a PC running along side XP and Vista and it let me choose how much of the left over drive to install Ubuntu on. 

When I get to the part on where to install it comes up with just my whole internal hard drive in the box. Also it has the second option about using the most free space, which it just has the drive I have OS X installed and the 3rd one is there to manually do the partition and I can never get past that part.

Do I need to format that partition something else besides the Mac OX Extended (Journaled) I formatted it as? Then would it show up in the first option?

Thanks

---

### Post by Nick_Jinn on 2010-07-22
You probably formatted it to format that Ubuntu cant install to. You are going to have to use the installer to create formats that it can use.

Go to the manual configuration option, delete the partition you made, create a new / partition (15gb or more maybe) and a larger home partition. Use the options they provide you.

Mac OSX is better about reading Linux files than Windows is right? If that is the case you probably wont need a third shared partition for storage, though you optionally can make one with Gparted.

---

### Post by flatlined on 2010-07-22
I've read I think it is that you can get away with just the 2 partitions the / and home partition. If so how would i divide up 15GB between the 2?

Thanks

---

### Post by Nick_Jinn on 2010-07-22
Thats kind of small for both partitions. If you are using a size that small I wouldnt even divide them. Just use the 'install side by side' option and use the slider to specify the size you want. That is more space efficient size you are sharing the space and either / or /home can write to the same space.

---

### Post by flatlined on 2010-07-22
I don't get the install side by side option. When I first loaded off DVD it just gave me the Erase the intire drive I can't get the install side by side so I did the partition and that didn't come up either should I reformat the partition MSDOS or is there a way to get the install side by side option?



> **Nick_Jinn said:**
> Thats kind of small for both partitions. If you are using a size that small I wouldnt even divide them. Just use the 'install side by side' option and use the slider to specify the size you want. That is more space efficient size you are sharing the space and either / or /home can write to the same space.

---

