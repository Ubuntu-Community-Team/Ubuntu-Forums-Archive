---
title: "Defragmentating?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by nwkegan on 2007-08-06
I've searched through the forums and have not found a definitive answer to my question, which might be attributed to my poor searching skills, nonetheless, I'd like to ask my question at the risk of sounding stupid.

Does linux fragment files? I'm talking ubuntu, I installed the 7.0.4 ISO, that's all I know. Whatever the 7.0.4 ISO is that you get when you go to the ubuntu site and then click download, thats what I have.

If it does, does it do it enough to warrant defragmentation? If so, what software should I use to do so? Thanks.

---

### Post by Inxsible on 2007-08-06
linux does fragment files when you are using more than 90% of the hard drive(guesstimate). But even then fragmentation is not too bad in Linux file systems (ext3 ext2 etc)

---

### Post by Steveway on 2007-08-06
Most filesystems used by Linux, most common are ext3 and Reiser3, only start to fragment if they are about 95% full.
If you access a Fat or a NTFS drive through Linux it will become fragmented very fast, this is more a failure in the filesystem than in the operating system.

---

### Post by SPQQKY on 2007-08-06
> **Steveway said:**
> Most filesystems used by Linux, most common are ext3 and Reiser3, only start to fragment if they are about 95% full.
If you access a Fat or a NTFS drive through Linux it will become fragmented very fast, this is more a failure in the filesystem than in the operating system.
Question, sorry to thread steal. Do you mean the NTFS file system you are accessing will become fragmented or the ext3, reiser3, etc., file system will become fragmented? I like to save files to my storage drive, access files from my storage drive which is NTFS. 
If my linux file system is becoming fragmented, what is best way to defrag?

---

### Post by Inxsible on 2007-08-06
Like steve said, fragmentation is more a problem of the file system rather than the OS. so it doesnt matter whether you are accessing a FAT or NTFS drive thru linux or windows, it may get get equally fragmented. 

The difference lies in how the file system handles files and how they store them on the drives. Turns out, that EXT3 is a lot better in handling fragments compared to FAT or NTFS.

---

### Post by SPQQKY on 2007-08-07
Okay, well I haven't experienced any problems. Ubuntu seems much faster with everything I do compared to windoze (boot time, ripping cd/dvd, accessing files, etc.) and I only use windoze for the occassional game of if someone needs to use my computer and they need to see windoze or they freak out....lol. thanks again.

---

### Post by nwkegan on 2007-08-07
okay, that brings me to another qusetion...

are extended partitions a bad idea? my linux partition is only 25 gigs and i want to expand it without reinstalling, which im guessing the only way is through extended partitioning. does that slow the system down or hurt it in any way?

---

### Post by Inxsible on 2007-08-07
no, i dont think it slows down the system or anything. in any case you cannot have more than 4 primary partitions on a drive, so you definitely need extended partitions if you want to have more than 4 partitions.

---

### Post by nwkegan on 2007-08-07
whats the difference between a primary and logical partition?

I installed linux on (I THINK) a logical drive, not sure if thats possible, a google search says it isn't, and I used the gnome partitioner to create an ext3 partition, so maybe it automatically made it a primary, but if it IS possible, will it create any complications?

---

### Post by davidsrsb on 2007-08-07
So far as Linux goes, not much. Windows likes to install on a primary partition. 
There is no limit to how many logical partition you have, so it is possible to have multiple OS, eac with its own /boot, /var etc

---

### Post by Inxsible on 2007-08-07
read more about partitions [here ]("http://en.wikipedia.org/wiki/Partition_%28computing%29")on the wiki. ubuntu can be installed on extended partitions. In fact, I have installed my /(root), /home and swap all on the extended partition. No complications whatsoever.

---

### Post by nwkegan on 2007-08-07
thank you all for your replies.

I've got one more question. if I created another partition to store files on, could I start installing linux programs onto it? through the package manager, how would I change where it installs, or can I at all? if so, I'm sorry I already asked but I want to be aboslutely clear, will extending the linux partition slow it down in any way? and if not, how would I do that? the gnome partitioner doesn't seem to be able to, and partition magic doesn't support it.

Thank you so much for your replies, this community is very helpful!

---

### Post by schorsch on 2007-08-07
> There is no limit to how many logical partition you have, so it is possible to have multiple OS, eac with its own /boot, /var etc
Of course there is a limit: If you are using SCSI-Devices, the maximum number of partitions is 15; using IDE devices you are limited to 63 partitions at all .......

---

### Post by nwkegan on 2007-08-07
> **nwkegan said:**
> thank you all for your replies.

I've got one more question. if I created another partition to store files on, could I start installing linux programs onto it? through the package manager, how would I change where it installs, or can I at all? if so, I'm sorry I already asked but I want to be aboslutely clear, will extending the linux partition slow it down in any way? and if not, how would I do that? the gnome partitioner doesn't seem to be able to, and partition magic doesn't support it.

Thank you so much for your replies, this community is very helpful!

I'd like to add another question to that, is there anyway to back up my settings for ubuntu? also, whats the default ubuntu called, when you download it directly from their site?

---

### Post by ronny_d on 2007-08-07
Read / look at this:


[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

rather a long url... but i read it once and it makes things clear between linux and windows (or maybe you even already saw it?)


I remember i in a far away dark past had to use 'defragmentation' on some ms-windows and i did it a few times, i never understood it, really never. When i started to use Linux i never had to use any defragmentation, which made me happy, and it made me glad that in Linux there was not even a tool for it which told me that it was the OS itself that was taking care of itself. I did not have to worry about "cluttering disk's content" which windows had given me the impression of continuously (what about that 'blue screen' that i have only heard of but never seen?).  

But so maybe the above url could enlighten you...

---

### Post by cobrn1 on 2007-08-07
So many questions, so little time...

Vista doesn't like to be installed on a logical drive (although apparently you can install it to a primary partition, and then convert it to a logical drive and it will still work - don;t know how to do it though... sounds a bit like a petty way to stick two fingers up at MS, but whaterer :D ;))

Linux, as far as i'm aware, can be installed on a logical drive if you like, and it won't make a fuss. Googling it doesn't really give a conclusive answer, but i'm 99% sure that it can be done, just like you'd install it on a primary partition...

As far as I was aware (I read the article posted above a few years back) the linux file systems are designed in a superior way to NTFS and FAT, so they rarely fragment.

As goes installing, I think the answer is no (but in a good way...) To the best of my knowledge, unlike in windows, the place where programs are installed is predetermined with linux programs. AS long as you have the linux partitions mounted then it will automatically install the programs there as if it was all one partition.

However, if you are running out of room on your main partition this is bad, because you are still stuck. Maybe try resizing the current linux partition using gparted cd?

What exactly do you mean by extending the linux partition? If you mean using the gparted cd to increase it's size then no, there will not be any slow down... I don't see how you can extend it otherwise tho (unless you make a separate /home partition in the extended space, etc). Again, you won't see any slow down.

Default ubuntu? maybe you mean the ubuntu live CD x86 7.04 CD? That's one way of describing it... Care to elaborate on what you mean.

Anyway, if you want help working out your partitioning you're going to have to tell the size of your hard drive and the current layout of the partitions...

Have a look at the GParted CD (download and burn the .iso).

If you give us that info then we may be able to help you further...

Backup isn't really my area of expertise (I'd guess at backing up the .folders in your /home/user directory, but I'm not sure) so I'll defer you to someone elses guidence

***question - how can he back up his settings?***

consider this a bumb :D

---

### Post by kokopelli69 on 2007-08-20
Hello All,

I'm actively using Winxp, Ubuntu & openSUSE and because of windows, I need to be able to defrag my system. As you can imagine, I can't change all my file systems to ext3 to get over  this defrag problem.

With that said, do you guys know of any well known/supported defrag tools in Linux that will defrag file systems other then Linux file systems? I know this was asked before and I know it's not really needed for my Linux partitions.

If anything, it would be a nice tool for anyone trying to move from windows world. :~>

Thanks guys....
Chris
kokopelli69 at gmail dot com

---

### Post by Aishiko on 2007-08-20
I'd be intrested in haveing a Defraging tool for the just in case senario, I mean I don't think it would be very big and not use up anything but what 10-30 meg of storage at the worse?

---

