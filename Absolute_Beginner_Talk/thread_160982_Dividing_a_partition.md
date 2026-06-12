---
title: "Dividing a partition"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by mevets on 2006-04-16
Hi, I ran into yet another problem while trying to setup a dual boot that i cannot find an answer too.

I get as far as choosing a partition. The only partition usable is my 77.0 GB, which is the second partition. Windows also resides here. I tried to config the Size of the partition but when I came to the resizing prompt I was unsure weather:

1. I was defining the size of the new ubuntu space
2. I was defining the lower size of the the pre-existing windows space

Now that i think of it... I was just defining how much windows space and once lowered my "free contiguous" partition would enlarge or a similar result, correct?

I'm off to try that, please correct me if I'm wrong. Even reassurance that this is the correct process would be apriciated.
[COLOR="Red"]Did that. The result of which is 17.0 GB, I only need a little alotted to Ubuntu, of unusable (for the #2 partition, windows). At this point should I go ahead and choose the bottomward selection "Write to partition?" I'm too scared to proceed so I figure I'll wait for advice. Thanks.[/COLOR]

P.S. - I installed Ubuntu on a different and old failing computer and Ubuntu works wonderfully.

---

### Post by gerbman on 2006-04-16
[QUOTE=mevets]Hi, I ran into yet another problem while trying to setup a dual boot that i cannot find an answer too.

I get as far as choosing a partition. The only partition usable is my 77.0 GB, which is the second partition. Windows also resides here. I tried to config the Size of the partition but when I came to the resizing prompt I was unsure weather:

1. I was defining the size of the new ubuntu space
2. I was defining the lower size of the the pre-existing windows space

Now that i think of it... I was just defining how much windows space and once lowered my "free contiguous" partition would enlarge or a similar result, correct?

I'm off to try that, please correct me if I'm wrong. Even reassurance that this is the correct process would be apriciated.
[COLOR="Red"]Did that. The result of which is 17.0 GB, I only need a little alotted to Ubuntu, of unusable (for the #2 partition, windows). At this point should I go ahead and choose the bottomward selection "Write to partition?" I'm too scared to proceed so I figure I'll wait for advice. Thanks.[/COLOR]

P.S. - I installed Ubuntu on a different and old failing computer and Ubuntu works wonderfully.[/QUOTE]I'm not quite following your situation, but from what I do understand you have Windows on a 77GB partition (#2). What is partition 1? I think the most straight-forward way to do what you want is to resize your Windows partition before running the installer. Then, when you run the installer, choose to manually edit the partition table. Tell the installation to _not_ use the windows partition, but to install to the free space that resulted from the resize. It should take care of setting up the boot loader so you can boot both OSes. Of course, it's always a good idea to back up your data before messing with the partition table. It's pretty easy to mess things up.

Help at all?

EDIT:  You'll need at least two partitions created in the free space during installation, one for the OS and one for swap space. Generally, people make the swap space twice the size of their system RAM.

---

### Post by mevets on 2006-04-16
My partitions:
[QUOTE=mevets]
#1 primary 57.7 mb fat16 /media/hda1
#2 primary 60.0 GB ntfs   /media/hda2
    unusable 17.0 GB
#3 primary 3.0 GB fat32   /media/hda3
#4 primart 8.2 MB ext3
[/QUOTE]
My problem is that what should be free space is labeled unusable. The guide I'm following along with says there can only be 4 primary partitions, could this be why the space is being deemed unusable?

---

### Post by gerbman on 2006-04-16
[QUOTE=mevets]My partitions:

My problem is that what should be free space is labeled unusable. The guide I'm following along with says there can only be 4 primary partitions, could this be why the space is being deemed unusable?[/QUOTE]I'm not totally sure, but it could be because the free space isn't at the end of the drive. Do you need partition number 4? It's only 8MB, and if you can do without it you could boot the LiveCD, run GParted, delete partition #4, and move partition #3 towards the beginning of the drive to put the free space at the end (GParted won't move ext3 partitions).

---

### Post by xyz on 2006-04-16
Hi-
I found this guide quite clear. 
[http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)

---

### Post by Mustard on 2006-04-16
You can only have 4 primary partitions.  The way around it would be to turn one of the four partitions into an extended partition (I'm pretty sure this would entail data loss on that partition), and from within that extended partition you could have several logical partitions.

---

### Post by catlett on 2006-04-16
What program is calling the 17gb unusable? Is it a partition that is unformatted? I ask because 1, if it is still in NTFS formaf it cannot hold a linux system. Or 2, it is not formatted at all. Sometimes the partitioner will have an error and will divide the partition but bot format the new one. In that case it is unallocated space. You then have to make a partition with that space. The 4 primary partition limit can be worked around by making the new one logical.

---

### Post by steve.horsley on 2006-04-16
[QUOTE=mevets]My partitions:
> Originally Posted by mevets
#1 primary 57.7 mb fat16 /media/hda1
#2 primary 60.0 GB ntfs /media/hda2
unusable 17.0 GB
#3 primary 3.0 GB fat32 /media/hda3
#4 primart 8.2 MB ext3

My problem is that what should be free space is labeled unusable. The guide I'm following along with says there can only be 4 primary partitions, could this be why the space is being deemed unusable?[/QUOTE]
Do you actually need what is on partitions 3 and 4? I'm fairly sure hte 17G is unuseable because you have already allocated all 4 primary partitions. I would be inclined to delete partitions 3 and 4, and add a logical partition instead. That way, you can chop the remaining 20 G into as manp partitions as you want. Or just delete 3 and 4, then let the installer use all the available free space.

---

### Post by mevets on 2006-04-16
Got it to work. Thanks for the help!

---

### Post by gerbman on 2006-04-16
[QUOTE=mevets]Got it to work. Thanks for the help![/QUOTE]What was the solution?

---

### Post by xyz on 2006-04-17
**every question you may ask on any site might be an answer to somebody else's pbm once you figured out how to solve it,so be so kind as to post how you did it!...even if it didn't work.**...
I've had,more often than I wish,a real pbm posting because I don't know the right words.I get shy and I don't thread!It's only human (Ubuntu) and this is the place where it is "Hubuntu" H as in Human...as far as computer life goes!
If you just "forgot" to post your solution, forget what I just said. You also may not have had time to tell us about it.

---

### Post by mevets on 2006-04-18
I ended up having to delete my partitions 3 and 4. Once I did that The space became usuable.

I should say that I did not completely follow the guide. I opted not to set aside space for a FAT32 file system. I autoconfigured the partition and, if I can remember correctlly, it came up with 600 MB of Swap space. From there I just wrote the changes to the disk.

---

### Post by xyz on 2006-04-18
thanks!glad it worked one way or the other.

---

