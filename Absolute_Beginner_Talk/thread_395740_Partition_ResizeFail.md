---
title: "Partition Resize:Fail"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by BogFrog on 2007-03-28
My friend had been nagging me for weeks to switch over from Windows to Linux. So after awhile i got pretty interested. He gave me the "Live Ubuntu" disc, i slid it in, clicked install. I go to resize my partition to save to 10g of free space...click apply... error. The goal of the "operation" was not to erase windows from my computer i wanted to keep windows along with Linux on my computer at once. However, I kept getting a message, I don't remember exactly what it said, it basically just said theres a problem and go figure it out yourself. So basically nothing i did to my partitions would save/apply. I use a Dell: INSPIRON 9300 laptop computer. Could this problem be do to Dell's security system on my computer preventing me from adding a new operating system to my computer? I would really appreciate any suggestions because i am very interested in running Ubuntu on my computer along with Windows. 

(i created a swap partition, thats not the problem)

---

### Post by Doug11 on 2007-03-28
> **BogFrog said:**
> My friend had been nagging me for weeks to switch over from Windows to Linux. So after awhile i got pretty interested. He gave me the disc, i slid it in, clicked install. I go to resize my partition to save to 10g of free space...click apply... error. The goal of the "operation" was not to erase windows from my computer i wanted to keep windows along with Linux on my computer at once. However, I kept getting a message, I don't remember exactly what it said, it basically just said theres a problem and go figure it out yourself. So basically nothing i did to my partitions would save/apply. I use a Dell: INSPIRON 9300 laptop computer. Could this problem be do to Dell's security system on my computer preventing me from adding a new operating system to my computer? I would really appreciate any suggestions because i am very interested in running Ubuntu on my computer along with Windows.

Did you create a swap partition as well? You must have a "/" partition which will be your main Ubuntu partition but you must have a swap partition of at least,,i think 256mb,,before youUbuntu will install. If this is the error, it will tell you the min size of a swap partition.

---

### Post by BogFrog on 2007-03-28
Yes yes, i did make a swap, and i left plenty of space, and i clicked apply and it would not apply

---

### Post by deathbyswiftwind on 2007-03-28
If you used a live disc this was a known bug for alot of people. Download the "alternative" install cd and use that works like a charm.

---

### Post by c-breakdown on 2007-03-29
Where would I find the "alternative" install cd?  Do you mean the previous version?

---

### Post by indytim on 2007-03-29
Better yet, download and burn the iso to a CD for GParted Live.  That will give you a boot CD to set up you partitions **before** you install Ubuntu or Kubuntu.  Btw- it's a nice tool to have available anyways.

IndyTim

---

### Post by dstew on 2007-03-29
If the partitioner would not apply the operations you selected, there can be several reasons. Sometimes, the partition you want to resize has not been defragmented, and there are pieces of files in the part you are trying to free up. Another reason is bad sectors on a partition. If it is a Windows partition, you can boot into Windows and run chkdsk /f on the Windows command line to fix them.

I also recommend using the GParted live CD for doing partitioning before installing, especially if you think you might become a linux nut and will go about installing on computers far and wide...

---

### Post by mcduck on 2007-03-29
The most likely reason is indeed the fragmentation on the windows partition. Start windows in safe mode and run defrag, after that the Ubuntu installer should be able to resize the partition with no problems.

---

### Post by c-breakdown on 2007-03-29
Thanks for all the things to try guys, I seriously appreciate it.

I have defragged twice so far, but I will try defragging in safe mode I guess.  I'm downloading GParted live CD right now and I'm going to run chkdsk /f also.  I'll let you know how it goes.

---

