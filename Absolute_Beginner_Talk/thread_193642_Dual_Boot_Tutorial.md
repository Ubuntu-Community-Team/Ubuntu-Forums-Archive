---
title: "Dual Boot Tutorial"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by gatoruss on 2006-06-10
I am a total Linux newbie, and am a computer novice.  The whole concept of Linux interests me, but I have been hesitant to to install for fear of disrupting windows (XP).  Well, my HD has crashed, and I will need to reinstall windows so I was thinking this might be a good time to try a linux install and install both in a dual boot format.  It will be on an AMD system.  I thought I'd give Ubuntu a try.  I tried some searches, but did not find something directly on point (on a borrowered PC, so my search time is limited) - on this forum (although I did find some info on dual booting redhat and xp and debian and xp on google).  Can someone direct me to a tutorial for setting up Ubuntu and XP in a dual boot format?  Or will following the redhat or debian tutorials suffice?

Thanks in advance!

Gatoruss

---

### Post by ????? on 2006-06-10
Try reading [this to see how to dualboot windows with ubuntu](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by gatoruss on 2006-06-10
Thanks!  That is helpful.  It seems to assume that windows is already installed.  Should I reinstall windows first, then install Ubuntu?  I will be using a brand new HD?

---

### Post by ????? on 2006-06-10
Install windows first, and when you get to the partition step in Windows Install, leave some space for Ubuntu.

---

### Post by gatoruss on 2006-06-10
Thanks for bearing with me.

The primary HD is 80GB (SATA).  What would be your recommendation for partition?  How much space should I leave for XP and Ubuntu, respectivly.  

Note, I have a 200GB (IDE) secondary drive that I use for data storage (image files, downloads, backups, word docs, etc.).  Am I correct that the file system on my secondary drive might be the wrong type for Linux?  I believe it is FAT?  If so, should I partition this drive as well and create a Linux-friendly file system for storage?
 
I really do appreciate your help.

---

### Post by berng on 2006-06-10
I installed Ubuntu two weeks ago on my Windows machine. I allocated 30 gb which I got from my primary drive. I'm currently using 3.5 gb. In your case you can allocate 50 to 60 gb from your primary for windows leaving the remainder for Ubuntu or you can take the space from your second drive by shrinking the that windows partition. I used partition magic to shrink the windows partition for my needed 30 gb.

When you install Ubuntu, the partition manager will ask you where to get the Linux disk space from. I took the option to use the unallocated free disk space.

---

### Post by grsing on 2006-06-10
For the primary, the XP size kind of depends on how many programs of what size you're planning on installing.  I guess I'd just split it up 40/40 (well, 40/39/1, with the 1 for the Linux swap).  40GB will be well more than you need for Linux, so if you're planning on lots of programs in windows, you could easily go as low as 10 GB for Linux.  If the secondary drive is already in FAT, that's perfect.  Both Windows and Linux can read and write to it, so it's ideal for sharing things between them (Linux can read NTFS, the normal XP filesystem, but writing is still kind of experimental; Windows can't read ext3 or any of the other Linux filesystems).

---

### Post by aysiu on 2006-06-10
If you're thinking about how to divvy up your partitions, read this:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by gatoruss on 2006-06-10
Thanks to everyone.  This is very helpful and informative.  I think I am going to like this community if everyone is as helpful to newbies as you each have been!

Okay, I looked over the information in the link that aysiu provided.  Seems the scenerio with a "/home partition" is the best as it seems to give most flexibility on upgrades in the future.  I presume that that is where the actual operating system for Ubuntu is installed?  And that Ubuntu programs are installed in the Ubuntu/ext3 partition?

Also, in follow up to a prior statement I made, I was wrong.  My secondary drive is NTFS.  What can I do now?

Thanks.

---

### Post by aysiu on 2006-06-10
[QUOTE=gatoruss]Thanks to everyone.  This is very helpful and informative.  I think I am going to like this community if everyone is as helpful to newbies as you each have been![/quote] It's the main reason I use Ubuntu and not Mepis.

> Okay, I looked over the information in the link that aysiu provided.  Seems the scenerio with a "/home partition" is the best as it seems to give most flexibility on upgrades in the future. Well, yes, as you have the option to upgrade or do a clean reinstall, with little adverse effects either way. > I presume that that is where the actual operating system for Ubuntu is installed?  And that Ubuntu programs are installed in the Ubuntu/ext3 partition? Actually the programs and operating system are installed on the **/** partition. The **/home** partition is where your personal settings and files live. > Also, in follow up to a prior statement I made, I was wrong. My secondary drive is NTFS. What can I do now? It's a 200 GB drive, right? How much of that is full?

---

### Post by gatoruss on 2006-06-10
> Actually the programs and operating system are installed on the / partition. The /home partition is where your personal settings and files live. 

From the standpoint of allocationg partition space, therefore, of the "portion" of the drive I allocate to Ubuntu, I should allocate a majority to the **/home** as it seems that this would take up more space than the actual operating system?

> It's a 200 GB drive, right? How much of that is full?

Yes it is 200GB, and approximately 50 to 70 GB are used.  It is entirely data - image files, software downloads, back up of pst files and the like.

I will need some time I think to figure out how to download and install Ubuntu.  My primary HD crashed and needs to be replaced.  I will need to reinstall windows.  I am trying to start that as soon as I can so I can have internet access, and get the wife email access so she will stop asking, "does my email work yet" :-)  Right now I am "borrowering" my daughter's PC to access this site.

---

### Post by aysiu on 2006-06-10
[QUOTE=gatoruss]From the standpoint of allocationg partition space, therefore, of the "portion" of the drive I allocate to Ubuntu, I should allocate a majority to the **/home** as it seems that this would take up more space than the actual operating system?[/quote] Yes, that's the general idea. Right now, in addition to random programs I have installed, I have Ubuntu, Kubuntu, and Xubuntu on one partition, and the total disk space use is 2.8 GB.

So allowing something like 8 GB for Ubuntu would have your bases covered, especially with as much hard drive space as you have.

> 
Yes it is 200GB, and approximately 50 to 70 GB are used.  It is entirely data - image files, software downloads, back up of pst files and the like. Well, what you could do, then, is a little juggling...

1. Shrink the NTFS to 70 GB.
2. Format the remaining 130 GB as Ext3.
3. Copy the 70 GB of used info to the 130 GB part.
4. Format the first 70 GB as Ext3.
5. Copy the 70 GB from the 130 GB to the 70 GB portion.
6. Delete the 130 GB partition.
7. Extend the 70 GB partition to fill up the whole 200 GB.

---

### Post by gatoruss on 2006-06-10
```
So allowing something like 8 GB for Ubuntu would have your bases covered, especially with as much hard drive space as you have.
```

So if I went with the recommendation above to allocate 30GB of my 80GB primary to Ubuntu, then how does the following strike you?
[LIST]
[*]48GB XP
[*]10GB /
[*]20GB /home
[*]2GB Swap
[/LIST]

I also have a 300GB external HD - I am storage paranoid :-)  I could just transfer 70GB to external, format 200 and then transfer the 70GB back, correct?  I am assuming that you are suggesting that I make the entire 200GB EXT3 and then install FS-Drive so XP can read/write to that drive?  Had not heard of FS-Drive until I say your link, don't know much about it or how it works.

Thank you very much for your help.

---

### Post by aysiu on 2006-06-10
Hm. Actually, if you have a separate drive just for storage, your /home partition doesn't really have to be so big, but I don't suppose it'd hurt.

2 GB for swap is overkill, though. Swap should generally be 2 times your RAM, but if you have 1 GB of RAM, you probably will *never* need swap.

And, yes, you could just copy over to the 300 GB to reformat your 200 GB hard drive.

I'm proposing to format the 200 GB as Ext3, since that's a journaled filesystem that can support large files (files bigger than 4 GB), but you can also format it as FAT32 if you don't want to install the FS-Driver on Windows.

I've used the FS-Driver myself, and it works flawlessly, but I do realize some people have reservations about it, for whatever reason.

---

### Post by gatoruss on 2006-06-10
Thank you.

---

