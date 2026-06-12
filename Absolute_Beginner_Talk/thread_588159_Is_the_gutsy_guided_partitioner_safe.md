---
title: "Is the gutsy guided partitioner safe?"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by whiffy badger on 2007-10-23
I've just had a very bad experience with a partition manager which trashed my windows partitions so I'm looking to be sure that the guided partitioner on gutsy is completely safe.  I will be dual booting with XP.  Any feedback on this "guided partitioner" would be appreciated.

Thanks

---

### Post by dangerpl on 2007-10-23
I personally never had problems with it, and I did a lot of dual-booting. But it's very important to backup all your data. It can never be stressed enough. People often forget to do that and after running into problems often lose their imprtant data. Guided partitioning is safe. Make 3 partitions, one for root(/) one for your home directory and one for swap. So if your system fails your home directory will be safe on another partition :) Good luck!

---

### Post by brk3 on 2007-10-23
The ubuntu partition manager has always worked 100% for me and everyone I know. If in doubt use the 'manual' option so you have full control over what gets resized.

---

### Post by dougleduck on 2007-10-23
While I don't know how often things go wrong I never had any problems with the partitioner. I'd read some of the tutorials floating around on partitioning if your new to linux.

I know most people would strongly recommend you backup all important data before using a partitioner, then if it doesn't go perfectly you will only have lost time.

---

### Post by dangerpl on 2007-10-23
I apologize. That's what I meant to say. Use manual partitioning. You have more control over your partitions.

---

### Post by dangerpl on 2007-10-23
Guided partition will erase all your data including your XP. I strongly suggest manual partitioning.

---

### Post by forestpixie on 2007-10-23
I shied away from the guided partitioner myself, wasn't completely sure of the wording. Used the manual partitioner after that, but now do it before install with gparted.

---

### Post by whiffy badger on 2007-10-23
Thanks for your replies!  So the guided partitioner isn't  a good idea.  I'm a bit of a linux noob, does anyone know of a really good guide, hopefully not too complicated that shows how to partition using the manual option.

Thanks

---

### Post by Sef on 2007-10-23
> I'm a bit of a linux noob, does anyone know of a really good guide, hopefully not too complicated that shows how to partition using the manual option.

Read [Psychocat's Installing]("http://psychocats.net/ubuntu/installing").

---

### Post by ukripper on 2007-10-23
Personally I would use manual partition to create  /(root) and Swap partitions. much easier..
[https://help.ubuntu.com/community/forum/installation/Partitioning](https://help.ubuntu.com/community/forum/installation/Partitioning)

---

### Post by mivo on 2007-10-23
Without a separate /home partition re-installing is much more tedious and time consuming. There are so many people who had issues with upgrading from 7.06 to 7.10, and their best option is to re-install. Would be painless with a separate /home partition.

---

### Post by ukripper on 2007-10-23
Even if you don't use seperate home partition it is still easy to copy /restoreyour data over from your backup to your new home directory so don't worry about that.

---

### Post by mivo on 2007-10-23
It's still extra time, and some people do not have external drives or a second box to backup gigs of media files to. :) (this was a recurring theme in the "upgrade troubles" type of threads). I think 10 GB for / and the rest for /home works well for the majority of users. For Gentoo I would make a separate partition for /var (it compiles the sources there) and if I knew I was going to install a larger number of commercial, native Linux games (Windows games go to /home) I'd make / larger, but I think the above layout is fairly straight forward.

---

### Post by ukripper on 2007-10-24
From beginner's perspective it would be alot to go through creating that amount of partions and directories. I would suggest any beginner using Linux just create  **/ , home and Swap **for starting. (/home can be optional and could be later created on seperate partiion once gained enough experience on linux but as suggested above it is good idea to create /home partiton before installation).
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by hyper_ch on 2007-10-24
The guided partitioner isn't dangerous but one really has to read... same goes for manual partitioner... if you don't read stuff you're likely to do something wrong... even if you've done it countless times before.

And the golden rule is: ALWAYS MAKE A BACKUP FIRST

---

### Post by forestpixie on 2007-10-24
> **hyper_ch said:**
> The guided partitioner isn't dangerous but one really has to read... same goes for manual partitioner... if you don't read stuff you're likely to do something wrong... even if you've done it countless times before.

And the golden rule is: ALWAYS MAKE A BACKUP FIRST

No the guided partitioner isn't dangerous - or at least no more so than any tool used correctly - but I for one wasn't completely sure which partition was going to have the quoted size - logically I expected the resized partition to be the one quoted. 

And I could find no information at the time to clarify the first time I used it, you just have to hope that it is working how you'd expect it to. I'm not saying that it's a bad tool - just a bit terse with info on the one thing that could make the whole installation a complete nightmare. 

I still think that making, resizing and deleting partitions is better accomplished prior to installation if that option is available. If nothing else it means that you can concentrate on the job in hand.

Totally agree with the backup though, many times have I told people over and over again - only to not have an up to date backup when I needed one :oops:

---

### Post by mivo on 2007-10-24
[GParted]("http://gparted.sourceforge.net/") is easier to use and less confusing, I feel. In case of Kubuntu the standard partitoner also bugged and calculates the size of the disk incorrectly (so for the last partition there is not enough space even though the partitioner says there is, and then still throws error messages), though that may have gotten fixed in 7.10.

---

### Post by forestpixie on 2007-10-24
totally agree which is why I pointed him there earlier :) - I haven't used the new gutsy version though supposedly it's newer than feisty's - I do it all with gparted live.

---

### Post by R_U_Q_R_U on 2007-10-24
Even without a separate /home partition, the easiest thing I found is to copy my /home to a USB hard drive. The 100 plus GB drives are very inexpensive and make backing up tons of data very easy. This is the cheapest insurance you can get and you will not have to come back here posting messages about how you lost all your music and photos because "Ubuntu ate my partition."

HTH

---

