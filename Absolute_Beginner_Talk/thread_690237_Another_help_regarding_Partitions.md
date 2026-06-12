---
title: "Another help regarding Partitions"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-07
In summary, right now I have **1 hard disk**. It's **100 GB**. *Divided into 2 by default*, namely **ACER **and **ACERDATA**. Both are **50 GB**.

Now, normally by default, **Windows XP** is installed in **drive C:** ... something happened so I then decided to *install another* **Windows XP**, **in drive D:** ... Now that is my** default OS**. I *deleted ***Windows XP** in **drive C:** manually, but still, my important files are still there, since I'm into *Video Editing*.

On** drive D:**, I have **3-4 GB** of *free space*. On **drive C**:,** 3-4 GB**, but I am planning to backup some of my files so I can have some free space.

Anyway, example, I will install **Ubuntu**, can I use the free space of **C:** to install it, without deleting the stored files? If possible please give me instructions.

Later after the installation and testing **Ubuntu**, I am planning to boot back to **XP**, then backup my files, then delete them from the hard disk.

Is it possible to **resize **the **partition **again, so that I can have more space for my **Ubuntu **installation or OS? Still, retaining the files?

How can I do that? Do you think I need to use **Partition Magic**? Also, can **Partition Magic**, can act similar or does it have a feature like **Super Grub Disk**?

Please help, really excited to install it!!! Please!:lolflag:

---

### Post by bumanie on 2008-02-07
Whatever partition you install ubuntu to, will be formatted to ext3, therefore if the partition contains any files, they will be deleted by the format. Instead of uxing partition magic, it would be better to use the live cd, gparted for your partitioning needs. Windows, generally will boot best best from the first partition of a drive, gparted will move the partition to the 'beginning' of the drive for you. I'm not sure what this will do to the mbr of windows though. I would make sure that you have backed up everything that is important to you before doing anything.

---

### Post by sandysandy on 2008-02-07
> **karlo said:**
> In summary, right now I have **1 hard disk**. It's **100 GB**. *Divided into 2 by default*, namely **ACER **and **ACERDATA**. Both are **50 GB**.

Now, normally by default, **Windows XP** is installed in **drive C:** ... something happened so I then decided to *install another* **Windows XP**, **in drive D:** ... Now that is my** default OS**. I *deleted ***Windows XP** in **drive C:** manually, but still, my important files are still there, since I'm into *Video Editing*.

On** drive D:**, I have **3-4 GB** of *free space*. On **drive C**:,** 3-4 GB**, but I am planning to backup some of my files so I can have some free space.

Anyway, example, I will install **Ubuntu**, can I use the free space of **C:** to install it, without deleting the stored files? If possible please give me instructions.

Later after the installation and testing **Ubuntu**, I am planning to boot back to **XP**, then backup my files, then delete them from the hard disk.

Is it possible to **resize **the **partition **again, so that I can have more space for my **Ubuntu **installation or OS? Still, retaining the files?

How can I do that? Do you think I need to use **Partition Magic**? Also, can **Partition Magic**, can act similar or does it have a feature like **Super Grub Disk**?

Please help, really excited to install it!!! Please!:lolflag:

as brought out by bumanie you should first backup your data from C:/ drive.
 if ur win XP is running from D:/  u can easily access C;/ drive and back up ur required data.
If u want, u can also use live CD of Ubuntu to boot up and then access ur C:/ drive. U can then backup.
just remember if u do any installation on C;/ drive whether it is windows or Linux u will loose all data. so backup before installing.
enough data backup softwares are there. just google to find one that suits u.
with gparted Cd u can boot up and resize partitions as required.

regards

---

### Post by karlo on 2008-02-07
> **bumanie said:**
> Whatever partition you install ubuntu to, will be formatted to ext3, therefore if the partition contains any files, they will be deleted by the format. Instead of uxing partition magic, it would be better to use the live cd, gparted for your partitioning needs. Windows, generally will boot best best from the first partition of a drive, gparted will move the partition to the 'beginning' of the drive for you. I'm not sure what this will do to the mbr of windows though. I would make sure that you have backed up everything that is important to you before doing anything.

Is it possible that, let's say I have this spaces on the end of the disk. Can I just use the spaces on the end of the disk, convert it into a new partition? I don't have the DVDs to back them all up... Is Partition Magic 8.05 not good with Ubuntu?

---

### Post by erfahren on 2008-02-07
> **karlo said:**
> Is it possible that, let's say I have this spaces on the end of the disk. Can I just use the spaces on the end of the disk, convert it into a new partition? I don't have the DVDs to back them all up... Is Partition Magic 8.05 not good with Ubuntu?
3-4GB will not be enough space for the partitioner to work with. It does need space to move data around (just like defragging). Clear off that C: drive to give yourself a little more to work with. 

To use those two sections of free space you'd need to move the D: partition up into some of the C: - a dramatic move for such little space and critical data to move. You really should back up before doing anything anyway.

Its not recommended to use non-Linux partitioners to create partitions - there was an article about that...

anyway, the Ubuntu LiveCD contains a excellent partitioner called GParted, boot up into the CD and launch it through System > Administration > GParted (or press Alt+F2 and type in "gksudo gparted") - if it asks for a password just hit "enter" (I think).

it sounds like most of your data is video files - so it shouldn't be too fragmented. It would probably be a good idea to run Windows Check Disk on the C: partition a couple times before resizing it.

(go steal a couple DVDs from a friend)

---

### Post by phr0ze on 2008-02-07
Free up about 8GB on Drive C. Then defrag that drive 2 times. Then boot the ubuntu CD. The Ubuntu installer can automatically resize drive C and make room for a new partition on the end. Just make sure you pick the right drive.

I've done this several times in the past. And even though these programs have worked fine before, you should ALWAYS back up your files. A DVD costs less than 25 cents. How much is your data worth to you if you loose it?

Thanks,
John

---

### Post by karlo on 2008-02-07
> **sandysandy said:**
> as brought out by bumanie you should first backup your data from C:/ drive.
 if ur win XP is running from D:/  u can easily access C;/ drive and back up ur required data.
If u want, u can also use live CD of Ubuntu to boot up and then access ur C:/ drive. U can then backup.
just remember if u do any installation on C;/ drive whether it is windows or Linux u will loose all data. so backup before installing.
enough data backup softwares are there. just google to find one that suits u.
with gparted Cd u can boot up and resize partitions as required.

regards

Are you really sure? What abou the feature that you can make a partition of the free space on C: without loosing the data?

---

### Post by karlo on 2008-02-07
> **erfahren said:**
> 3-4GB will not be enough space for the partitioner to work with. It does need space to move data around (just like defragging). Clear off that C: drive to give yourself a little more to work with. 

To use those two sections of free space you'd need to move the D: partition up into some of the C: - a dramatic move for such little space and critical data to move. You really should back up before doing anything anyway.

Its not recommended to use non-Linux partitioners to create partitions - there was an article about that...

anyway, the Ubuntu LiveCD contains a excellent partitioner called GParted, boot up into the CD and launch it through System > Administration > GParted (or press Alt+F2 and type in "gksudo gparted") - if it asks for a password just hit "enter" (I think).

it sounds like most of your data is video files - so it shouldn't be too fragmented. It would probably be a good idea to run Windows Check Disk on the C: partition a couple times before resizing it.

(go steal a couple DVDs from a friend)

I downloaded GParted LiveCD, is it a good decision? I defragmented it, still Windows says that I should defrag it. By the way the free spacei s now 10 GB :guitar: ...

... but after installing Ubuntu, I'll boot back to Windows XP, then delete some more if possible, then GParted again and adjust the partition again ... **will this be possible**?

Where can I run Windows Check Disk? I am also researching for a software, third-party one to defrag my hard drive.:)

---

### Post by karlo on 2008-02-07
> **phr0ze said:**
> Free up about 8GB on Drive C. Then defrag that drive 2 times. Then boot the ubuntu CD. The Ubuntu installer can automatically resize drive C and make room for a new partition on the end. Just make sure you pick the right drive.

I've done this several times in the past. And even though these programs have worked fine before, you should ALWAYS back up your files. A DVD costs less than 25 cents. How much is your data worth to you if you loose it?

Thanks,
John

You are right, I went back to the store yesterday, I was pissed of because many are buying s DVD/CDs too, the stores offers the cheapest removable storage devices including CDs and DVDs, but unfortunately, many are buying at the same time, which made me stuck for more than an hour, but I have to go because I have to get home and do some more important things. Time is very important to me...:(

---

### Post by erfahren on 2008-02-07
> **karlo said:**
> Are you really sure? What abou the feature that you can make a partition of the free space on C: without loosing the data?that's true - but rule number one: there are no guarantees

also, as I mentioned, you don't have enough room to work with - there was someone else awhile back who was have trouble resizing and had more free than you do. 

when resizing the partitioner works like defrag does in a way - it moves data and needs room to work with

I don't understand why you'd want to risk *altering* your partition with so much critical data on it in the first place.

If you are really set on doing it without removing some to a backup then maybe "clean house" a little.

---

### Post by erfahren on 2008-02-07
ok - nevermind my previous post then (I type slow)

Use the Windows Check Disk ("Error Checking") - right-click on the drive in "My Computer" and go to "Properties" and then the "Tools" tab - run it a couple times - it's been my experience that all the errors won't be fixed the first time through.

Then to defrag - use this little standalone defrag utility (it's free): [http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)
it doesn't need to be installed - just put it somewhere (like just in C:\ ) and run it. Exit as many running processes you can when running it - antivirus, firewall, etc. - it doesn't look like much - but does a much better job than the Windows one.

---

### Post by karlo on 2008-02-07
> **erfahren said:**
> ok - nevermind my previous post then (I type slow)

Use the Windows Check Disk ("Error Checking") - right-click on the drive in "My Computer" and go to "Properties" and then the "Tools" tab - run it a couple times - it's been my experience that all the errors won't be fixed the first time through.

Then to defrag - use this little standalone defrag utility (it's free): [http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)
it doesn't need to be installed - just put it somewhere (like just in C:\ ) and run it. Exit as many running processes you can when running it - antivirus, firewall, etc. - it doesn't look like much - but does a much better job than the Windows one.

After minutes of researching, based on [http://forums.cnet.com/5208-6142_102-0.html?forumID=5&threadID=58776&start=225](http://forums.cnet.com/5208-6142_102-0.html?forumID=5&threadID=58776&start=225) ... I downloaded **PerfectDisk Rx Suite**. Majority said that you only need it to run once and it'll do the rest.

Oh yeah, I recovered 2 GB more, 12 GB of free space!:popcorn: (still downloading PerfectDisk)

What if after installing Ubuntu, I want more space, let's say I recovered additional spaces, can I resize the partition where Ubuntu is installed without deleting or touching the files?:(

---

### Post by erfahren on 2008-02-07
> **karlo said:**
> After minutes of researching, based on [http://forums.cnet.com/5208-6142_102-0.html?forumID=5&threadID=58776&start=225](http://forums.cnet.com/5208-6142_102-0.html?forumID=5&threadID=58776&start=225)
What if after installing Ubuntu, I want more space, let's say I recovered additional spaces, can I resize the partition where Ubuntu is installed without deleting or touching the files?:(
yes - you can use GParted to do that. It's on the Ubuntu LiveCD.

---

### Post by karlo on 2008-02-07
> **erfahren said:**
> yes - you can use GParted to do that. It's on the Ubuntu LiveCD.

**even if** Ubuntu is **currently** *installed*?

---

### Post by erfahren on 2008-02-07
yes - [GParted](http://gparted.sourceforge.net/) is included on Ubuntu's LiveCD. You would boot up into the LiveCD and launch GParted (I think it's off the menu > System >Administration).

anyway, since it would be running off the CD you can have better access to the hard drive.

It can move partitions as well as resize them. You can look at its documentation for more information and screenshots.

---

### Post by bumanie on 2008-02-07
There is always some potential risk if one is changing/resizing partitions etc. I can honestly say that I have moved, resized, and copied partitions with gparted and up to this point in time, have never lost any information or ruined a file system with gparted. It is a very good tool. But nothing is foolproof 100% ie if there were a power outage when gparted was half through its job - you would end up with a wrecked file system. There is only a small chance of that happening, but it is possible.

---

### Post by 3pinner on 2008-02-07
I'll admit right off that I'm brand new at this, and had a similar situation with a lot of critical stuff  on my HD running Windows that I could not alter or lose. 
What I  did was just go get another hard disk. I connected the new disk as my first one in the system (this is a SATA drive, if you have the regular IDE, make it the master) and installed UBUNTU to that one. 
Worked great! Ubuntu loaded fine, the boot loader (GRUB) was loaded there instead of on the Windows drive. Nothing was touched on the Windows drive, and I can move files to the Ubuntu one at will.

---

### Post by karlo on 2008-02-11
> **erfahren said:**
> yes - [GParted](http://gparted.sourceforge.net/) is included on Ubuntu's LiveCD. You would boot up into the LiveCD and launch GParted (I think it's off the menu > System >Administration).

anyway, since it would be running off the CD you can have better access to the hard drive.

It can move partitions as well as resize them. You can look at its documentation for more information and screenshots.

I've burned the live cd, and now running Ubuntu, without deleting my files, although I have another question, i'll post it later, regarding to extending my current ubuntu partition, for more space...

---

### Post by karlo on 2008-02-11
> **bumanie said:**
> There is always some potential risk if one is changing/resizing partitions etc. I can honestly say that I have moved, resized, and copied partitions with gparted and up to this point in time, have never lost any information or ruined a file system with gparted. It is a very good tool. But nothing is foolproof 100% ie if there were a power outage when gparted was half through its job - you would end up with a wrecked file system. There is only a small chance of that happening, but it is possible.

GParted did a wonderful and tremendous job!!!!

---

### Post by karlo on 2008-02-11
> **3pinner said:**
> I'll admit right off that I'm brand new at this, and had a similar situation with a lot of critical stuff  on my HD running Windows that I could not alter or lose. 
What I  did was just go get another hard disk. I connected the new disk as my first one in the system (this is a SATA drive, if you have the regular IDE, make it the master) and installed UBUNTU to that one. 
Worked great! Ubuntu loaded fine, the boot loader (GRUB) was loaded there instead of on the Windows drive. Nothing was touched on the Windows drive, and I can move files to the Ubuntu one at will.

Ok, you did right, to be safe. But what about laptops?

---

