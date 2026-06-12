---
title: "Trying to re-partition my hard drive"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by thelugnut on 2007-11-18
I have a "250 GB" hard drive, partitioned as follows: 

I have Windows XP on one partition, (/dev/sda1) using 56.85 GB, and

Ubuntu 7.10 on another partition, (/dev/sda3) using 60.21 GB.

I have another partition (/dev/sda2) using 60.62 GB, formatted to ntfs and empty.

Finally, I have an "unallocated section, using 52.60 GB.

It can be seen then, that I have over 111GB of hard disk doing nothing.

What I want is for this 111 GB area to be assigned to the Ubuntu installed O.S.

Is there any way I can reassign this area to Ubuntu?

I have looked at Gparted but haven't been able to ascertain what I should do.

I have read the various tutorials on partitioning, but again, didn't come up with a solution.

Help would be much appreciated.

---

### Post by Pumalite on 2007-11-18
Post a screenshot of your Gparted.

---

### Post by kiepmad on 2007-11-18
I'm not 100% sure, if I understood your problem.
But I think what you need to to is:
* Backup your system in some way (never play around with partitions without back-up ;) I felt it )
* System ->Preferences ->Partition Editor
* Select the empty nfts partition. Unmount it.
* Delete the partition

You now got non-continuous space after your ubuntu partition.
You must resize this partition. I don't know if this is possible while the partition is still mounted. You may try.

---

### Post by mdpalow on 2007-11-18
Don't think you can resize it while in use.

Think you'll need to run Partition Editor from your Live Disk.

---

### Post by thelugnut on 2007-11-18
Pumalite wrote:

> Post a screenshot of your Gparted. 

How do I do that?::confused:

kiepmad wrote:

> You now got non-continuous space after your ubuntu partition.

The Ubuntu partition is located all the way to the right. The Windows XP partition is located all the way to the left.

The other two partitions are in the middle.

As I understand it, following your instructions would leave me with the 111 GB section in the middle. How would I combine this section with the Ubuntu partition?

Thanks to you both for the replies.

mdpalow wrote:

> Don't think you can resize it while in use.

Think you'll need to run Partition Editor from your Live Disk.

O.K. I'll keep that in mind, for the time being. Thank you.

---

### Post by Pumalite on 2007-11-18
Use Gparted Live CD: [http://gparted.sourceforge.net/downlod.php](http://gparted.sourceforge.net/downlod.php)
It's an iso. Burn as image to CD. Boot from it. It will show your partitions and it has utility to take screenshot.

---

### Post by sandysandy on 2007-11-18
> **thelugnut said:**
> Pumalite wrote:



How do I do that?::confused:

kiepmad wrote:



The Ubuntu partition is located all the way to the right. The Windows XP partition is located all the way to the left.

The other two partitions are in the middle.

As I understand it, following your instructions would leave me with the 111 GB section in the middle. How would I combine this section with the Ubuntu partition?

Thanks to you both for the replies.

mdpalow wrote:



O.K. I'll keep that in mind, for the time being. Thank you.

with gparted there is option to move your partitions to left or right. 
also u can reformat your ntfs empty partition to ext3 if u want. the option is there in gparted.
if u want just one extra partition for ubuntu, u may consider deleting the empty NTFS partition so that u have one contiguous free space, which u can then partition using gparted and format as ext3. u can mount it as /home if u want for all ur personal files of ubuntu.

Keep it in mind that its always advisable to BACK UP data before partitioning.

regards

---

### Post by bumanie on 2007-11-18
I was going to tell you how to attach a screenshot, unfortunately I am at work and in front of a windoze machine. However, I think you go applications --> accessories --> take screenshot is in drop menu.
Attach to post by going to 'manage attachments' under additional options towards the bottom of this page, that is the post page.
If you are using the gparted live cd, I think there is a take screenshot option in its menu's.

---

### Post by thelugnut on 2007-11-18
I will try to get the screen shot displayed.

---

### Post by Pumalite on 2007-11-18
Explain to me again what you want to do with which partitions.

---

### Post by thelugnut on 2007-11-18
As you can see, there are  two center partitions, one formatted to ntfs and the other unallocated.

I would like to combine them and add them to the Ubuntu partition, located on the far right.

The end result would be two partitions, (not counting the "swap"), one for windows xp and the second large one for Ubuntu.

---

### Post by HokeyFry on 2007-11-18
looking at the screenshot, isnt the max number of partitions on one disk 4? if so, i dont think you can create another partition without moving all of the data starting with /dev/sda2 onwards to the left. Then you might be able to add another one to the extended partition, but i dont know how an extended partition works or if youd even be able to run an OS from it.

[This page should help you out a great deal in knowledge of this though]("http://www.pcguide.com/ref/hdd/file/structPartitions-c.html")

---

### Post by Pumalite on 2007-11-18
You can save the data in the middle ntfs, then delete it and make it unallocated, then extend the ext3 to the left (right click, resize)

---

### Post by thelugnut on 2007-11-18
I don't have to worry about saving any data on the ntfs partition. I don't have anything there.

So I delete the ntfs partition, which will then combine with the unallocated partition, and then format those combined paritions. Is that about it?

---

### Post by Pumalite on 2007-11-18
No. Extend the ext3 partition to the left occupying the unallocated space.

---

### Post by thelugnut on 2007-11-18
O.K. I think I have it.

Can't thank you all enough for your replies and your patience in answering.

Thank you  :)

---

### Post by thelugnut on 2007-11-18
I followed your directions and am happy to report that everything worked out just fine.

I would like to thank you again for steering me through this.:)

:guitar:.

---

### Post by Pumalite on 2007-11-18
Cheers. Happy Ubuntuing!

---

