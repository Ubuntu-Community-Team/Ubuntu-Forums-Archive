---
title: "Will Ubuntu Install?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by fatla00 on 2007-03-23
I have a 120 GB hard disk. My C: is 98.7 GB which I have Vista installed on and I have a 12 GB D: that I'm just using for storage right now. If I moved data from my D: to C: and started up the Ubuntu installation, would I be able to just erase what ever data/formatting, etc. is on the partition and install Ubuntu on it from the installation? And once that is complete, is there some way from inside Ubuntu I can resize the partitions without messing Vista up?

Thanks in advance.

---

### Post by dfreer on 2007-03-23
> would I be able to just erase what ever data/formatting, etc. is on the partition and install Ubuntu on it from the installation?
Yep. You will probably need to manually edit the partition tables when you install, delete the 12 GB. From there, give yourself a small partition for your swap, and then allocate the rest of the 12 GB to Ubuntu.

About Vista, I do not know how Ubuntu plays with Vista's File system. 
You might want to try this article out:
[http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/)

---

### Post by fatla00 on 2007-03-23
Thanks for the response.

What do you mean by "giving yourself a small partition to swap?" From the 12 gb, do you want me to create another 1gb partition? If that's what you said, what's that for?

And I read that, thanks, it's actually that I am having problems with.

---

### Post by Campingman on 2007-03-23
I used the info in this site, 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
explains all the partitions you need for install, you can do at the time of install by selecting manually edit partitions and you should still be able to get internet access to check you are doing it correctly.  Now that has got to be a lot better than Windows!

---

### Post by bigkahoona on 2007-03-23
> **dfreer said:**
> About Vista, I do not know how Ubuntu plays with Vista's File system.
If only there was such a thing as a "Vista File System". Microsoft - Master of Innovations that they are - are still banking with that last century file system NTFS.

:lolflag:

[quote=fatla00]What do you mean by "giving yourself a small partition to swap?"[/quote]
The swap partition in Linux/Unix is what the pagefile.sys is in Windows, only that it has its own partition instead of being slapped into the system partition. When your machine runs out of physical memory, the system uses space on the harddrive instead (which is sloooooow).

---

### Post by dfreer on 2007-03-23
Ok, some swap general info. You can skip this if you just want to get going but learning is always a good thing. This won't be perfectly correctly but should give you a basic idea of what swap is.

Basically, when you open a text file what actually happens is that the file is read from the hard drive and copied to RAM. When you make changes to the file, all of those changes are performed in RAM, with the original file still on the hard drive unaltered. When you finally save the file, you are overwriting the original file on the hard drive with the one in RAM.
Although it gets a lot more complex with programs and the operating system itself, this is basically what RAM is used for, as a temporary holding space. Well, sometimes your RAM gets full of information, or the information in RAM isn't being used. Your OS will take that information and write it to a special place called the swap file, partition, or drive. It is basically another temporary holding space, except it reads/writes alot slower than RAM does. Windows has a swap file which is generally located at C:\pagefile.sys. Linux likes to have a entire partition dedicated to the swap file.

So basically for good performance you will want a swap file, especially if you do not have a bunch of RAM. A good rule of thumb is that your swap file should be 1.25-1.5 times the amount of RAM you have. For example, with 512 MB's of RAM your swap file should be around 1.25 GBs.

These are the only two needed partitions for Ubuntu, the swap partition and the / partition. So when you get around to installing Ubuntu, Delete the 12 GB partition (get your data off first!!!), make 2 new ones, one for your swap and one for your root or /

> And I read that, thanks, it's actually that I am having problems with.
Your having problems with a Microsoft Product!? *shock* lol, unfortunately I haven't tried resizing Vista. I know I have heard that Partition Magic does not play nice wwith vista at all, which is the only way I would resize XP. Try googling around and searching this forum, if you can't find a way come back here and dedicate a thread to it. Above else make sure to post your solution back here at your original thread, so that other's you find your post through googling will know what to do :D

---

### Post by dfreer on 2007-03-23
> **bigkahoona said:**
> If only there was such a thing as a "Vista File System". Microsoft - Master of Innovations that they are - are still banking with that last century file system NTFS.

:lolflag:

Didn't they use a *new* version of NTFS? It surely isn't the exact same file system, is it? *horrors* Hmmm I think I would rather them use NTFS then to create something completely new that Linux can't even read...

---

