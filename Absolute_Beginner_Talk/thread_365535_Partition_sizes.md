---
title: "Partition sizes"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-02-19
I want to install Ubuntu 6.06 dual-boot with Windows XP on my computer. I have a 80 GB hard drive with about 30 GB of space used.  How much space should I give to Ubuntu.  I want to use the graphical installer.  I don't know much about partitioning so I don't want to do any manual partitioning.  Will the installer make the swap, etc. partitions for me?

(P.S. What purpose does the swap partition serve?)

---

### Post by moshuptrail on 2007-02-19
If you don't want to do manual partitioning, then let the installer do it.  In that case, I'm not sure what the question is.

Assuming you have 50G left for Ubuntu after shinking NTFS to about 30G I suggest the following:
1G - swap (used when total of all programs exceed RAM size)
5-10G - /   (your depending on how many programs you think you will install)
20G - /home (use the remainder for personal files & accounts)

But really, I strongly suggest manual partitioning with the Gparted LiveCD.  Even if you don't use the Live CD, I still recommend doing it in two passes from the installation CD.  First partition and format, then run the install and let it use your defined partitions.

---

### Post by Onyx_47 on 2007-02-19
Ubuntu can do everything by itself if you want to, during the installation just tell it to use the largest continous (sp?) space available...

I recommend you to edit the partitions manulay thought, don't worry, it's graphical and not hard at all. Create a partition for Ubuntu and format it as ext3, then make another one for swap and format it as, well, swap.

Swap is like PageFile in Windows. Go with 1GB, I think you won't need more...

---

### Post by bodhi.zazen on 2007-02-19
Boot to windows, defragment

Then boot the Ubuntu Live CD, start gparted.

Gparted will re-size your windows partition. 

Make some new partitions for ubuntu root and swap

Swap = RAM X 2, max 1 Gb

Root partition = 10 Gb will be just fine :)

PS Swap is used to extend your RAM onto the hard drive when your system runs out of RAM. No having a large swap will not increase performance ;)

Here is a nice how-to : [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by xpod on 2007-02-19
Defrag Windows a couple of times then use gparted on the Ubuntu cd to resize the Win partition down to whatever you want but just leave it un-allocated...Then run the actual installer and tell it to use the largest continuous free space once it gets to the partitioning stage and it will do the rest for you as you sit back and have a coffee

Or you can create all you partitions as advised above too:)

---

### Post by bigken on 2007-02-19
swap works the same way as virtual memory in windows if you run low on ram it will use the hdd 

if you have 50gig of spare space 

d
10 gig is good for /root 

point of thumb make your swap twice the size of your ram if you have 2gig 
you dont need a swap file 

whats left /home

---

### Post by Matt1632 on 2007-02-19
Ok, i'll use the manual partition editor in the graphical installer to make the partitions.  Is the root partition where I can save my files or is it just for programs?  Will GParted properly resize my windows partitions (i.e. It will move files if needed and it won't corrupt anything.)

---

### Post by bigken on 2007-02-20
you should defrag windows a couple of times 1st and backup any important data 

root is for the OS and home is where you save your files music ect the reason for the home partition is if you ever needed to reinstall ubuntu you only over write the root and and swap partitions so your files and stay safe in home :)

---

