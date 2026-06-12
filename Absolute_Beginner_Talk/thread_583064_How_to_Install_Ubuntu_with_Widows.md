---
title: "How to Install Ubuntu with Widows"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by UnBr34KaBl3 on 2007-10-20
I want to install Ubuntu on a Computer running Windows XP. I'll also want to keep XP and have booth Operating systems installed, I think It's called dual boot. I've noticed that I'll have to rezize the Partitions to do so. But I'm affraid that the entire computer will crash. I have the program for windows called Partition Magic and I've taken a Screenshot of it to show how the partitions are rigth now.

Here it is.
[IMG]http://img100.imageshack.us/img100/5718/partitionmagicscreenshout2.png[/IMG]

I guess that i should rezize the partition. But I'm not shure wich setttings I should use or pretty much anything.

If i make some free space on the hard drive(unallocated, I think its spelled that way, I hope you see what i meen). Is all I'll have to do after that to install Ubuntu from the CD?

When you run two operating systems, how do you change between them? Is it possible to make Widows start always if I'm not press a special button at startup that will make Ubuntu boot instead or something like that?

---

### Post by Duck2006 on 2007-10-20
This may help.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Paqman on 2007-10-20
First of all, welcome to the forum!

> **UnBr34KaBl3 said:**
> I think It's called dual boot.

It certainly is

> 
I've noticed that I'll have to rezize the Partitions to do so. But I'm affraid that the entire computer will crash. I have the program for windows called Partition Magic


Resizing partitions seems a bit daunting at first, but it's actually pretty straightforward. Ubuntu even has a partitioner built into it's installer, so you won't need to use Partition Magic.

> 
I guess that i should rezize the partition. But I'm not shure wich setttings I should use or pretty much anything.

If i make some free space on the hard drive(unallocated, I think its spelled that way, I hope you see what i meen). Is all I'll have to do after that to install Ubuntu from the CD?


First of all, back up all your important data from your Windows partition. From the sheer size of it, i'm guessing you have a lot of music and videos on there. Best to play it safe with all that.

Then defrag XP hard. Do a good cleanout, too.

During the Ubuntu install the built-in partitioner will shrink your XP partition and create the new ones Ubuntu needs.

> 
When you run two operating systems, how do you change between them? Is it possible to make Widows start always if I'm not press a special button at startup that will make Ubuntu boot instead or something like that?

Ubuntu installs a boot loader called Grub. When you first boot you'll be presented with the two systems to choose from. The default will be set to boot Ubuntu after a 10sec delay, but you can change the default, timings, etc.

---

### Post by justinmiller87 on 2007-10-20
I'm sorry, I have to say something; it's too funny not to.

> How to Install Ubuntu with **Widows**
Most importantly - remember one thing: don't be too pushy, especially if the person has recently become a widow. It's going to take a lot of time for them to be ready for something new, even if it is Ubuntu. Go slowly, but don't put a lot of pressure on them. Over time, they will open up and it will make it easier to talk them into trying it.

---

### Post by kamaboko on 2007-10-20
a word of warning.  a lot of people, including me, have not been able to get windows to load after using gutsy.

---

### Post by ukposter on 2007-10-20
Partition Magic should be able to deal with your situation well, without causing any damage to what you already have on your h/d. BUT, I do recommend that you back up anything on that h/d already that you regard as valuable(OS inc. updates, progs, files - pics, music, vids, docs etc.
 Resize a partition is what you need to use in PM, allow what is recommended by Ubuntu as a minimum size for installation + what space you can afford for any software and files that you think you will need space for while using Ubuntu. Also, remember that you may well be using a dual OS set up for some time and that you need space left for new Windows files and spare space for Windows to work in. Once you've decided that, set up the resize partition process to what you've decided on, the whole process is fairly intuitive and you should be able to do what you want with reasonable ease. I'm guessing that you have a certain amount of confidence in your abilities anyway, to be considering using PM.

The following is taken from PM's help files:
"To resize a partition

1	Select a disk and a partition.
2	Click Partition > Resize / Move.

The current size of the partition is shown on a disk map at the top of the dialog box. The map also depicts the used and unused space within the partition and the free space surrounding the partition (if any exists). The minimum and maximum sizes that you can resize a partition appears below the map.

3	Position the mouse pointer on the left or right partition handle.

The mouse pointer changes to a double-headed arrow .

4	Drag the handle to the partition size you want.
5	Click OK.

Tips

·	In step 4, you can also resize the partition by specifying new values in the Free Space Before, New Size, and Free Space After text boxes. The values you type may change slightly to values supported by your drive's geometry.

·	To make a partition smaller, unused space must exist within the partition. To enlarge a partition, there must be free space adjacent to it.

·	If desired, click the Cluster Size drop-down list and select a new size or use the recommend cluster size that is already selected. PartitionMagic changes the values in the Free Space Before, New Size, and Free Space After text boxes to show how the partition size is affected. This option is only available for FAT and FAT32 partitions. NTFS cluster resize is available in Partition > Advanced > Resize Clusters."

The PM help files should be able to deal with just about all that you need to know.

---

### Post by ddrichardson on 2007-10-20
> **kamaboko said:**
> a word of warning.  a lot of people, including me, have not been able to get windows to load after using gutsy.That's why you need to backup. I installed Gutsy on an HP notebook with Vista yesterday and there were no problems.

---

