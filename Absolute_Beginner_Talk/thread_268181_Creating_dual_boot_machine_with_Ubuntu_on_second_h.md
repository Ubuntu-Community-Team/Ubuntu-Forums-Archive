---
title: "Creating dual boot machine with Ubuntu on second hard drive"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Larriemac on 2006-09-29
I am using UBuntu on my HP laptap and desktop with no problems. I used the live CD to run Ubuntu on a third, older PC with two physical hard drive, Drive C: (9.8 gig) Drive D (16.0 Gig). Everything works fine uncluding recgonizing my wireless card and network with Live CD. However, when I try to install Ubuntu on the secod drive, I have problems. I like to give Ubuntu 8.0 gig and keep 8.0 gig as a Windows partition. GParted won't seem to let me partition this second drive as other than 560 meg and 15,6 gig. Tried several times and may be missing something simple. I am en experienced DOS/Windows user but new to Linux. I tried Red Hat Linux, early version, but it didn't seem to have drivers for my hardware.

I am currently downloading the alternate CD in case the partitioning part of it works any better. If not, I guess its back to fdisk.  I'd like to try the Ubuntu partioning product. Any help would be appreciated.

The PC is an older whitebox model, 733 MhZ, 256 ram, two hard drives, floppy, CD-Rom, Windows XP, trendware wirelss card.

Thanks

---

### Post by bulldog on 2006-09-29
Well 8GB isn't that much but I'm sure could be done.

Gparted should do the job very well.

But it's a little confusing when you use it the first time.

When you partitioning manually you must unmount the disk you want to manage.
Otherwise your settings want hold and you can't apply your new settings.

I suggest you read your steps twice to understand what's gonna happen.

---

### Post by Larriemac on 2006-09-29
Aha,

That mount/unmount thing went right by me. I'll try that.  Thanks

---

### Post by Larriemac on 2006-09-29
Well. That didn't work. It woun't let me "unmount" the drive, saying that "the directtory doesn't existr."

Is the alternate CD a better bet, or should I use DOS to repartition?

Thanks

---

### Post by bulldog on 2006-09-29
Can't say anything about the alternate cd,did and do all my partitioning with gparted and countered no problems yet.

But give it a try,it install's without the GUI so it would be much smoother.

---

### Post by louieb on 2006-09-29
The partitioning part of alt CD is similar to the live CD. It really doesn't matter which one you use. 
I am not an expert but I have installed Linux more that a dozen times in the last few months. This is what I would do. 

When you get to the partitioning part choose manual partitioning. 

When it gives you the list of your current partitions go through and delete all the current partitions on the second drive. This leaves the display showing 16 gig or so of free space.

Now you are going to create 3 partitions.
Partition 1 7.5 gig format ext3 mount point / . This where you will install Linux. Should be plenty of room. I have Ubuntu installed on a 4 gig drive.   
Partition 2. .5 gig format Linux swap.

That is all you need to do at this point. You can go ahead and assign the remaining space to a 3rd partition or you can wait till you fire up windows and do it through the disk manager.
Now you can go ahead and finish up your install.

This is a plan Jane partition scheme. If you look around you will see fancy schemes. This one is as simple as it gets and it will work.

---

