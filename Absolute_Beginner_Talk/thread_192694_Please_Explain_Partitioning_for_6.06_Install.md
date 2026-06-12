---
title: "Please Explain Partitioning for 6.06 Install"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by Trurl on 2006-06-09
Hi everyone,

   I'm taking my first steps into the linux world with Ubuntu 6.06, and after playing with the LiveCD for a while, I decided to try installing Ubuntu. I want to dual-boot with XP Pro. I have a 55.84 GB HD with 6.61 GB free. I was hoping I could simply install Ubuntu into 4 GB of the free space, but apparently things are not that simple. 

   I got to the partitioning step in the installation wizard and was not sure what to do. I tried to let the computer select the 'largest free continuous portion,' of the HD, but it told me it could not make a partition. Realizing I was out of my depth, I rebooted to windows, experienced a tense 10 minutes while my "dirty volume" was scanned and then sighed with relief as XP booted normally. 

  The case information presented, my question is how do I actually install dapper into the free space without damaging the windows side of my machine? I've read a number of different articles on installing dapper but none of them have done a good job explaining what partitioning really entails and how to do what I am trying to do. 

  Here are the specifics:

  I have an Inspiron 8600 Pentium M (1.5) with 768 MB of RAM and a 60 (55.8) GB HD. There are currently 6.61 GB of free space. I would like to give dapper between 4 and 5 GB of space. I do not know how much to allocate to the swap partition. 

    Essentially: How do I achieve the above goal (installing into a 4-5 GB partition) while preserving my XP Pro installation.

Thanks for your time and for any advice you could provide!

-Trurl

---

### Post by angkor on 2006-06-09
[http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)

Did you try this guide? It explains the partitioning as well.

---

### Post by elamericano on 2006-06-09
You should have seen an option "Resize partition (hda1) and use freed space" That's the one you want. You're installing from the LiveCD, right?

---

### Post by Trurl on 2006-06-09
Angkor: Thanks for the guide link! I'll check it out when I wake up. 

Elamericano: Regarding the "resize and use free space," I clicked on that and it showed a 51.5 GB partition. I wasn't sure if that meant that it wanted to give 51.5 GB to dapper or if that would be the windows side. If it corresponded to the windows side, would the wizard know to install to the other side? I am using the LiveCD. 

Thanks again,

-Trurl

---

### Post by elamericano on 2006-06-09
That's the size of your current Windows partition. Reduce that by 6GB to free up space for Ubuntu.

---

### Post by Trurl on 2006-06-09
Just checked the guide and it also suggest the resize option. However, when I selected that, it presented a 51.5 GB partition (in the orange bar) and this confused me because my drive is only supposed to have 55.8 GB of useable space BUT I know I have 6.6 free GB. 

Elamericano: This will probably sound stupid, but is what you're saying the following: select the resize option; it will then set the slider to 51.5 GB (96%); I should then move the slider down to 45.5 GB? I'm not sure I understand that. My machine has a 55.8 GB drive and I want to allocate between 4-5 GB to Ubuntu. When I select the resize option, where does the 51.5 GB setting come from? 

Does this question make any sense?

Thanks for your time.

-Trurl

---

### Post by az on 2006-06-09
[QUOTE=Trurl]
When I select the resize option, where does the 51.5 GB setting come from? 

Does this question make any sense?
[/QUOTE]

Yes.  Although you only have filled up your partition with 49 gigs of data (for example) it occupies more blocks since not every block is not neccesarily full.  You can try to defragment, but on a partition that full, you are bound to not be able to liberate all that much more space.

Maybe that is why you cannot create a new partition - the "free space" is probably not contiguous.

If after you defragment you still have problems, try freeing up some more space, if you can.

---

### Post by Trurl on 2006-06-09
Thanks for the defrag suggestion. At this point, defragging doesn't free up much more space. Will it be a problem if I choose the 'resize' option and go with what it decides? For example, if it tells me there is a 51.5 GB partition, can I just click "next" and be all right or do I need to resize the partition to make sure I don't hurt my XP install? 

I know these are basic questions, but I'm wary of messing around with my hard drive, and I appreciate the help.

Cheers,

Trurl

---

### Post by az on 2006-06-09
[QUOTE=Trurl]Thanks for the defrag suggestion. At this point, defragging doesn't free up much more space. Will it be a problem if I choose the 'resize' option and go with what it decides? For example, if it tells me there is a 51.5 GB partition, can I just click "next" and be all right or do I need to resize the partition to make sure I don't hurt my XP install? 

I know these are basic questions, but I'm wary of messing around with my hard drive, and I appreciate the help.

Cheers,

Trurl[/QUOTE]
It will ask you how small you want to shrink your parition.  It it cannot because there is no room or for other reasons (it's chicken) it won't do it.  It is not an aggressive partitioner - which makes it safe.

---

### Post by aysiu on 2006-06-09
[quote=Trurl]I posted earlier with questions about how to safely set up partitions. I'm still at it as my machine won't let me create a partition (I want to dual boot between XP and Ubuntu). I have a 55.8 GB hard drive and I have 9.47 GB free. However, when I tell ubuntu to resize the partition, it wants to resize to a 49.6 GB partition and it tells me my maximum hard drive space is 53.6 GB.

After about 10 minutes of waiting while it tried to create the partition, it informed me that there was no enough free space. How can this be and how do I install Ubuntu without hurting my XP install?

In my previous post, I was told to defrag and try again, which I have done, along with freeing up more space.[/quote] Can you post a screenshot of your GParted summary screen?

It would look something like this (see attached screenshot).

---

### Post by Trurl on 2006-06-09
Been trying to get to that point for a while (10 minutes). The installer seems to have stalled after I selected: "Manually Partition Drive." The little wheel is still spinning but nothing seems to be happening. If I ever get to the screen, I'll post it.

If I use the resize option, and I choose to decrease the partition size, won't that start to damage data already in that partition?


-Trurl

---

### Post by aysiu on 2006-06-09
No. It won't let you decrease the partition size to smaller than the data on it.

For example, if you had a 10 GB partition with 6 GB of data on it, the minimum you could resize it to would be 6 GB and a little bit.

This is why people tell you to defragment Windows before you resize it, but if it's a Linux partition, it doesn't need to be defragmented.

As for not being able to advance to the next step... well, it could be any number of things. I think the two most popular causes would be:

1. The CD you're installing with is corrupted. It got corrupted during the download process or during the burning process.
2. Your computer doesn't have enough RAM to be running a live session *and* installing or partitioning Ubuntu at the same time. If you have less than 256 MB of RAM, this could be the case, and you'd have to use the Alternate Installer CD.

---

### Post by Trurl on 2006-06-09
Restarted the installer and it worked this time. Unfortunately, no way to get the screen shot off the machine right now, so here is a verbal description:

/dev/hda1--fat16--47.04 MB--7.19 MB used--39.84 unused

/dev/hda2--ntfs--55.84 GB--46.36 used--9.48 GB unused--boot flag

unallocated--7.84 MB

__________________

No idea what the fat16 partition is...

I have 768 MB of RAM

Thanks for the help.

-Trurl

---

### Post by aysiu on 2006-06-09
Well, what do you want to do? If you want Ubuntu to be in the unallocated space, right-click on it and create a new partition of type **Ext3**.

---

### Post by Trurl on 2006-06-09
The unallocated space is only 7 megs, so unfortunately that won't work. What I want to do is to resize the ntfs windows partition down to about 47 or 48 GB and use the remaining space for ubuntu. I assume I need to allocate a swap partition as well? 

Also, when mounting, is it necessary to have a /documents?

Thanks,

Trurl

---

### Post by aysiu on 2006-06-09
Whoops! I'm sorry. I must have been reading GB, even though it said MB.

Go ahead and right-click on the NTFS partition and resize it as much as it'll go. Then you can right-click on the unallocated space and create partitions for / and /home and swap.

And a /documents partition isn't necessary at all. That's what I use instead of a /home partition, but most people use /home instead. Only my documents are important to me, not my settings as well.

---

### Post by Trurl on 2006-06-09
Thanks! I'll try that now. I think part of the problem is that my HD is currently fairly fragmented and there are no really large unallocated regions. Even defrag won't really help much since I have so much stuff already on the drive. 

I'll report back once something happens (hopefully something good)

What is strange is that every time I boot back into windows (after having been using the LiveCD) to try to free up more space , I get a message that my HD is dirty and scandisk checks it. Could this just be that the drive doesn't like the partitioning?

-Trurl

---

### Post by Trurl on 2006-06-09
Edit: I started a new thread, so to all of those who helped me in this, my thanks. I think my hard drive was simply too fragmented or some such thing. 
___________________________________________
I set the partitions up so everything seemed to match properly...in the middle of resizing the 55.8 GB partition to 45 GB, an error box appeared but it has no contents. It is a blank error box. Not sure what it means or what harm occured to my hard drive. I closed the error box and was brought back to the Gpart step. Here, it shows my my original partitions with GIANT YELLOW TRIANGLES OF MISERY and the words "Unknown" under filesystem. This, I take it, is bad. I've backed up the files I cared about, and was intending to re-install windows at some point, so I am not overly crushed. However, I have no idea what to do about the hard drive now. I suspect it must be completely reformatted, but I'm not sure the best way to do this. 

I still want XP and Dapper on the same machine. How should I go about this?

Thanks,

-Trurl

---

