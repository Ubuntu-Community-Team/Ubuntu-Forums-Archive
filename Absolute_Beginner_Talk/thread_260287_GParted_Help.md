---
title: "GParted Help"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2006-09-18
OK, here is the situation--I am trying to figure out how to partition my hard-drive using the GParted LiveCD (the version that comes with the Ubuntu LiveCD was causing trouble), and I know nothing about partitions or partitioning.

So, I would really like it if someone could point me to a recent article or tutorial that explains GParted and the whole process of partitioning in detail.  For instance, I have no idea what a logical partition is, if I can make my Ubuntu ones like that, or if one needs to be bootable, etc.

Rather than asking for suggested partitioning schemes, I'd really like to find out how GParted works completely, as well as how the whole process works.  Thanks! ^_^

---

### Post by xyz on 2006-09-18
Do you dual-boot? (XP-Ubuntu)?
[http://www.linux.com/article.pl?sid=06/04/25/1917228](http://www.linux.com/article.pl?sid=06/04/25/1917228)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Darklighter137 on 2006-09-18
I am planning on it, yes.  Thank you, friend, but I have actually read both of those articles.  Like I said, I am really confused and new to this whole thing. ^_^

---

### Post by xpod on 2006-09-18
It might not be the case for you but i had trouble using either Gparted on the Ubunto cd OR i`ts own cd for creating the initial XP partition.
This was most likely my ignorance but i opted for a 98 bootdisk with fdisk on it to do the initial XP part THEN i was able to use gparted on the live cd okay for the remaining Ubunto needs.

EDIT:I WAS able to create the partition ok but when it came to booting XP thats when i had issues as i had`nt set the partition as active.Not sure how i would have done that with Ubu live

---

### Post by bulldog on 2006-09-18
Your windows needs a primary Ubuntu can be installed everywhere.

I know it's confusing when you see it the first time,but it's not so hard to do.

First you have to decide how much space you want for XP and for Ubuntu.

When you made that decision it's time to get to work.

You can partition your hdd with the XP install cd but you only make the partitions you need for XP and leave the rest unallocated.

Install windows.

Pop in the live cd and boot into Ubuntu.

Push the install button and follow the on screen steps.

When you come to partitioning your hdd choose manual.

You see a screen with your hdd and your windows partition.
Be sure that its unchecked.

Now create a /  = [root] about 10 GB
Create a swap   = about 1-2 GB
Create a /home  = rest of the space

Push apply if you're sure it's the way you want it.
Now gparted is partitioning your unallocated space and will install Ubuntu the way you specificate.

That's all there is.

---

### Post by alecjw on 2006-09-18
Logical and primary stuff is confusing, but I'll try to explain.

On a hard disk, you can only have 5 (or is it 4?) primary partitions. Or 4 primary partitions and a a logcal drive, or 3 primary partitions and 2 logical drives etc. A primary partition is just a normal partition. A logical drive can contain an infiite number of partitions. To you could have 4 primary partitons and a logical drive. Inside that logical drive,  you can have another 10 extended partitions. So you have 14 paritions on a drive! Your computer can only boot from a primary partition, so you can't have ubuntu in a logical drive. You can however have your /home partition or your file sharing partition on a logical drive.

---

### Post by Darklighter137 on 2006-09-18
Okay, here are some things to note.  I have a GB of RAM, and a really creepy ~72 Mb space between my NTFS Windows partition and my  FAT32 recovery partition.  Will either of those things matter?  And, thanks again guys. ^_^

---

### Post by xyz on 2006-09-18
> **Darklighter137 said:**
> I am planning on it, yes.  Thank you, friend, but I have actually read both of those articles.  Like I said, I am really confused and new to this whole thing. ^_^

Sorry 'bout that!**Darklighter137**...it's not always for me to tell where people stand ...not being that far ahead myself!!
So about watching some videos?
[http://www.linux.com/article.pl?sid=06/07/20/1654251](http://www.linux.com/article.pl?sid=06/07/20/1654251)
Don't hesitate to ask questions even if you think it's "stupid"..we all are at times!

I see xpod's back in town! Gonna be hot tonite!!Hi there, mate! :)

---

### Post by alecjw on 2006-09-18
Nah. Just make the partitions bigger to fill the 72MB gap, and then shrink some partitions to make space for Ubuntu.

---

### Post by xpod on 2006-09-18
And of course theres THIS man`s way which will be much "simpler" than ANY way i ever get things done=D> :biggrin: 

GOOD LUCK

EDIT:> Logical and primary stuff is confusing, but I'll try to explain.

On a hard disk, you can only have 5 (or is it 4?) primary partitions. Or 4 primary partitions and a a logcal drive, or 3 primary partitions and 2 logical drives etc. A primary partition is just a normal partition. A logical drive can contain an infiite number of partitions. To you could have 4 primary partitons and a logical drive. Inside that logical drive, you can have another 10 extended partitions. So you have 14 paritions on a drive! Your computer can only boot from a primary partition, so you can't have ubuntu in a logical drive. You can however have your /home partition or your file sharing partition on a logical drive.


AHHHH NOW we understand.......LOL](*,) :biggrin:

---

### Post by bulldog on 2006-09-18
Tell us how large your hdd is and the amount of partitions,that will help alot.

Do you have a recovery disk,so you can delete you'r recovery partition?

---

### Post by Darklighter137 on 2006-09-18
Thanks, guys.  One last question--does the alternate CD provide a more reliable partitioning experience?

---

### Post by alecjw on 2006-09-18
If you're a beginner, you won't like alternate install. Text only. No graphics.

---

### Post by bulldog on 2006-09-18
> **Darklighter137 said:**
> Thanks, guys.  One last question--does the alternate CD provide a more reliable partitioning experience?

There's nothing wrong with the live cd.
You only have to understand how it's done,that's all.:biggrin:

---

### Post by Darklighter137 on 2006-09-18
Yes, I have a set of recovery CD's (16 of them!).  My hard-drive has about 160 GB, with 127 GB free

---

### Post by bulldog on 2006-09-18
16????? Okay that's enough to restore anything :biggrin: 

Is there a Windows cd among them?? just in case.

I presume you're not in for a full wiping of your hdd?:lol: 
Thought so.

Do yo have the opportunity to use Partition Magic?
Otherwise you can create a new partition with disk management in windows.

Defrag the hell out of windows 5 times should do it and create a partition as big as you want to use for Ubuntu.
Windows will format it  and choose FAT32 for it.

If done you can start installing ubuntu like posted before.

If you're a die-hard you can do all of this in gparted but I think you're more comfortable with windows.

---

### Post by Darklighter137 on 2006-09-18
Sadly, all 16 of those CD's are for restoring Windows; they were made by a utility that came with my PC.  I have all of my personal files on a USB memory stick.

What is this FAT32 partition going to be for?  I don't have Partition Magic, btw.

---

### Post by bulldog on 2006-09-18
Is not important really [FAT32 I mean] but it's easyer to determine the drive where you would install Ubuntu to.

If you have that much cd's it wouldn't be easy to restore your XP if something goes wrong.

And helping you on this distance is a risk,if you do a bad partitioning you could loose your XP.

That's not a big thing if you have an XP cd on your desk.

But there is nothing to it in fact,just read carefully what you're going to do and push only apply if you're absolute sure that it's all right and according to what you want to achieve.

Once you have done it you say, is that all??

---

### Post by Darklighter137 on 2006-09-18
So, sir, if I have understood you, this is what is to be done:
1. Resize my primary partition under Windows.
2. Create a new FAT32 partition.
3. Boot the LiveCD.
4. Change the file system to ext3.
5. Shrink that partition and create a /, swap, and /home.

Or did you mean I should just shrink the disk under windows, and then tell Ubuntu to use the largest free chunk of memory it can find?

---

### Post by bulldog on 2006-09-18
> **Darklighter137 said:**
> So, sir, if I have understood you, this is what is to be done:
1. Resize my primary partition under Windows.
2. Create a new FAT32 partition.
3. Boot the LiveCD.
4. Change the file system to ext3.
5. Shrink that partition and create a /, swap, and /home.

Or did you mean I should just shrink the disk under windows, and then tell Ubuntu to use the largest free chunk of memory it can find?

Step one is oke
Step two is oke {NTFS is oke too}
Step three is oke
Step four is not oke do nothing till you come to the partitioner by the installer.

Then you select manual partitioning.
Then you select the new partition and be sure that the XP not is selected.
Then you create a 10 GB /
Then you create a 1 or 2 GB swap [1 GB should be enough]
The rest of the space you make your /home


This is the important part,read carefully and look twice and if you're sure it's okay push apply and then there's no way back.
Gparted will partitioning according your settings and install Ubuntu.

---

### Post by bulldog on 2006-09-18
Or did you mean I should just shrink the disk under windows, and then tell Ubuntu to use the largest free chunk of memory it can find?
Reply With Quote

This is an option too but I prefere to do it manually.
Incase of a reinstall of Ubuntu you can keep your /home so your stuff is there.

But if you're a little offset,you can do it this way.
You can always try it again if the time comes you're more comfortable with Linux.

---

### Post by Darklighter137 on 2006-09-18
Thank you.  Before I make my decision, I will contact HP and see if they will give me a Windows XP Installation disk, which would make life much easier.  Thanks again. =)

---

