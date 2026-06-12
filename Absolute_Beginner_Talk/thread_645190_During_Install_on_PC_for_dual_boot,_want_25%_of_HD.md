---
title: "During Install on PC for dual boot, want 25% of HD partition"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by penguinv on 2007-12-19
During Install on PC for dual boot, want 25% of HD to be the Linux partition

When I get to the section it gives me a range of 50-100% of the hard drive. 
Since the hard drive is just over 50% full, I would like to give Ubuntu aoubt 10 GB or a quarter if the hard drive.

That's a lot more than the 2-3GB minimum I read about.

What's happening? What can I do?
Have I been operating unders some mistaken premise?


I have: Averatec 3255 XP pro AMD laptop, 512 M Ram, 40GB HD.

---

### Post by jken146 on 2007-12-20
There is a 'manual' partitioning option, where you can choose whatever you want.  You'll need a / partition (I would give this 10GB) formatted in ext3 and a swap partition (up to RAM x 2) formatted in swap.  You may also consider a separate /home partition so that you can reinstall without affecting your files (and some settings).

---

### Post by Yoke &amp; Chung on 2007-12-20
Hi,

If you are running Windows Vista, do not leave it to Ubuntu to re-partition your hard disk nor should you use any third party utilities (unless proven to work with Vista). 

Instead, you should use the Disk Management utility in Vista to shrink your NTFS partition first, then boot up live CD and proceed the Ubuntu installation. When you reach the partition screen, select "Use the largest continuous free space" option.

Regards

---

### Post by penguinv on 2007-12-20
First to Yoke and Chung:  I do not use Vista. I have Windows XP Professional. Quoting  the thread-starter. (But others may read this thread and need to notice the difference.)

> **penguinv146]I have: Averatec 3255 XP pro AMD laptop, 512 M Ram, 40GB HD.[/QUOTE]


Jken answered me: Thanks jken. And yet I want backup. Still want it. Repetition is how you avoid mistakes. Check it once - Check it twice.

[QUOTE=jken146 said:**
> There is a 'manual' partitioning option, where you can choose whatever you want.  You'll need a / partition (I would give this 10GB) formatted in ext3 and a swap partition (up to RAM x 2) formatted in swap.  You may also consider a separate /home partition so that you can reinstall without affecting your files (and some settings).

**Where can I read about this partition setup?** Do you know any links?
 I remembered something like this (needing to have more than one partition)  from messing with Slackware many years ago. Yesterday I read and searched a lot before I posted and could not find this information.

*I'd like to repeat what I understand from what you wrote* and add some concerns.

**1**. I want a partition "formatted in swap" of size 2x512 = 1024MB. 
--- I'd like to know why and what that does and why more is not better.
----and how to I format it in swap, I can infer a choice-list will appear but...

**2.** I want a partition formatted in ext3
----I want to allow 10 gigs total to Ubuntu so it would be 10G-1024 unless I do a /home partition
----What will go on this partition

**3.** It would be better to have a /home partition
----of what size, what will go there. Do I format it /home?
---how do I know I want these things?
 I read (yesterday I did a lot of reading about Ubuntu) that it is better to make only one partition so that you dont end up with unused space. On the other hand, I do understand what you are saying about reinstalling. I had a W98 machine I set up that way. The system could go down and all "my stuff" would still be safe.

Do I format added partition 2 and 3 the same? How does the Ubuntu installer know what in the filesystem to put on each part. Will it ask me? ((shiver)) because I will not know how to respond.

TIA

---

### Post by logos34 on 2007-12-20
I have same ram specs as you and I just shrank my swap down a few hundred megs from 1 gb because I never use even half that.  Unless you're doing video editing or graphics design, more than 1 gb is a waste.  Linux is much lighter than windows so you just don't need that kind of virtual memory. Plus with only a 40 gb drive you need to maximize space utilization.

Root: 7 or 8 gb is more than enough, IMO.  I have ubuntu studio with a lot of multimedia apps and my root is only 6.6 gigs, with 1.6 free. (I have a separate /home). That should be enough if you go with a separate home.

My thinking is evolving on the question of a dedicated /home partition.  If you backup everyhting regularly, then it really isn't needed. (especially when you have a fast external/auxiliary hard drive which makes backups painless and quick).   And with space at a premium in your case, I'd reconsider.  They're still nice to have--makes fresh installs and reinstalls a cinch.  But not when you're counting your gb's--more partitions = more wasted free space.

[http://www.easy-ubuntu-linux.com/ubuntu-feisty-installation.html](http://www.easy-ubuntu-linux.com/ubuntu-feisty-installation.html)
(installation w/ separate /home partition)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by jfinkels on 2007-12-20
> **penguinv said:**
> 
**1**. I want a partition "formatted in swap" of size 2x512 = 1024MB. 
--- I'd like to know why and what that does and why more is not better.
----and how to I format it in swap, I can infer a choice-list will appear but...

Linux uses the swap partition to write the contents of memory when your main memory (also known as RAM) "overflows". This might happen if you are running many processes which each require a lot of memory (like opening twenty firefox windows, each with a dozen tabs or something like that). Most of the time, when processes need memory, they get to use RAM, which is fast. When your RAM gets all used up, your processes get to use the swap partition, which is slow. You shouldn't need more than about 1 GB, because most of the time, you won't be using many memory-intensive programs.

The installer should prompt you about which filesystem to format the partition. Choose swap for your swap partition.
> 
**2.** I want a partition formatted in ext3
----I want to allow 10 gigs total to Ubuntu so it would be 10G-1024 unless I do a /home partition
----What will go on this partition

Here's info on creating a separate home: [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

I recommended just making one large partition if this is your first time installing. You can always change later on.

The installer may ask you a mountpoint for your partition. The mountpoint will be "/", the top-level directory of any Linux filesystem hierarchy. This is where the main operating system files, programs, data, etc. will go. After you install Ubuntu, you can put whatever other data you want on this partition, of course.
> 
**3.** It would be better to have a /home partition
----of what size, what will go there. Do I format it /home?
---how do I know I want these things?
 I read (yesterday I did a lot of reading about Ubuntu) that it is better to make only one partition so that you dont end up with unused space. On the other hand, I do understand what you are saying about reinstalling. I had a W98 machine I set up that way. The system could go down and all "my stuff" would still be safe.

Do I format added partition 2 and 3 the same? How does the Ubuntu installer know what in the filesystem to put on each part. Will it ask me? ((shiver)) because I will not know how to respond.

If you want to have a separate /home partition, you will need to format a new partition separate from the original partition designated (as described above) for "/", the root of the filesystem. You want to format your partitions with the "ext3" filesystem. It is a recent, stable, and efficient filesystem. If you're asked for a mountpoint, the mountpoint will be "/home". In your /home directory are your personal files. You have free reign over your personal /home directory, so this is roughly equivalent to "My Documents" in Windows, except better.

You won't really know if you want a separate /home partition until after you have used Ubuntu for a while, so I recommend that you don't bother with it. Again, you can always change later.

However, if you wish to have a separate /home, you will choose to manually partition your disk, and it will end up looking something like this:

5GB partition, formatted as "ext3", mounted on "/".
5GB partition, formatted as "ext3", mounted on "/home".
1GB partition, formatted as "swap", mounted as "swap".

Let me know if you have any more questions.

---

### Post by jken146 on 2007-12-20
> **jfinkels said:**
> 
However, if you wish to have a separate /home, you will choose to manually partition your disk, and it will end up looking something like this:

5GB partition, formatted as "ext3", mounted on "/".
**5GB partition, formatted as "ext3", mounted on "/home".**
1GB partition, formatted as "swap", mounted as "swap".

Why only 5GB for /home?  I would say use the whole of the remaining space.

---

### Post by jfinkels on 2007-12-20
> **jken146 said:**
> Why only 5GB for /home?  I would say use the whole of the remaining space.

Yeah, sure. Whatever. Doesn't matter. :D It was only an example. I briefly scanned the first post and saw "10GB" so I assumed there was approximately that much left.

---

### Post by penguinv on 2007-12-24
> **jfinkels said:**
> Yeah, sure. Whatever. Doesn't matter. :D It was only an example. I briefly scanned the first post and saw "10GB" so I assumed there was approximately that much left.

You are right. I only want to allocate 10 G total to Ubuntu. 
I will take the advice to start out with only 2 partitions, a swap and all-others partitions. That is how I understand it.

I am looking for help docs that are about understanding and not necessarily how to do it (separate question from the how to do it so I should ask this in a separate post). Just one or two paragraphs about what a kernel is, etc. Everything I find is way overboard. There are basics one has to get down first. 

Thanks for the help. I'll get back to the computer in question soon enough and actually try out the good advice.  Till then be merry and bright!

---

### Post by penguinv on 2007-12-24
> **penguinv said:**
> You are right. I only want to allocate 10 G total to Ubuntu. 
I will take the advice to start out with only 2 partitions, a swap and all-others partitions. That is how I understand it.

I am looking for help docs that are about understanding and not necessarily how to do it (separate question from the how to do it so I should ask this in a separate post). Just one or two paragraphs about what a kernel is, etc. Everything I find is way overboard. There are basics one has to get down first. 

Thanks for the help. I'll get back to the computer in question soon enough and actually try out the good advice.  Till then be merry and bright!

Once you have two systems on a machine the question comes up:
Can system 1 read the files on system 2?
I understand that Windows cannot read files written on the Linux partition.
I understand that Linux can read the files on the Windows partition.
Can Ubuntu WRITE on the Windows partition?

How does this relate to the "how to partition" question?
Easy, if I can save files on the windows partition I open up their use to both systems and extend the usefulness of the space allotted to Ubuntu.



Thanks from PV

---

### Post by penguinv on 2007-12-30
I;ve tried again to repartition my windows drive pursuant to installing Ubuntu and devoting 10G of a 40G HD to Ubuntu. I have learned that what I am about to do is** Resizing a Windows Installation.**

I saw that it is easy to tell a partion to be swap or whatever.
But after i asked for a swap it told me I had to do something permanent, then I went back and the list no longer showed my windows partition. 

[CENTER]_So I bailed again._[/CENTER]

[I]I have sucessfully used fdisk, partitioned drives, made logical and extended partitions in my past.

[CENTER]_Somehow it shouldnt be so hard_.[/CENTER][/I]

And somehow the default partitioning tool might know that only half of my HD is free. 
7.10 also gives me a choice of 40% to 100% of my hard drive to use, i dont get it. [CENTER]**It seems like a bug**.[/CENTER][http://www.easy-ubuntu-linux.com/resize-windows-partition.html](http://www.easy-ubuntu-linux.com/resize-windows-partition.html) does NOT show what I see. I dont get that option list.

And is it recommended to defrag first?

---

### Post by penguinv on 2007-12-30
Everything in my "few minutes ago" post stands.

I want to say: the best resource so far by far is [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) and it's the first one that is relevant, useful and not shallow. It addresses the issues I have been bringing up, what you have been telling me, and more. It discusses the partitioning decisions from more angles, bringing up extra things and helping me with what I brought up that nobody yet commented on.

That last was "can ubuntu write on a windows partition?". It brings up the idea of creating a FAT32 partition which both Windows and Ubuntu can read and write. It explains that while Ubuntu can read NTFS (XP style partition, and NT and 2000) it cannot write on one. And Windows is lost on all Unix style partitions but both do fine with FAT32. I believe FAT32 was late DOS style and has some limitations and was succeeded by NTFS.

In all of this not only should I get my partitions done without destroying my XP installation but others who install later could get a clearer cleaner path to install.  FYI I have backed up my data but Windows, plus all the stuff I have to download and install takes days. I don't relish doing it. But the next time I do it I will install _all_ the service patches immediately.

I'll be looking out for the next post.

---

### Post by Paqman on 2007-12-30
> **penguinv said:**
> 
That last was "can ubuntu write on a windows partition?"

If you're installing Gutsy Gibbon (7.10) then you certainly can write to NTFS partitions by default. Older versions will require you to install a package to get that ability. Don't bother with FAT32 partitions, because FAT32 is a very obsolete file system with some serious drawbacks.

And yes, Psychocats is excellent!

---

### Post by penguinv on 2007-12-31
> **Paqman said:**
> If you're installing Gutsy Gibbon (7.10) then you certainly can write to NTFS partitions by default. Older versions will require you to install a package to get that ability. Don't bother with FAT32 partitions, because FAT32 is a very obsolete file system with some serious drawbacks.

And yes, Psychocats is excellent!

Thanks for that. Also you revealed that I have to watch everything I read for relevance as well as accuracy. Arg. I knew that the LiveCD cant (didnt) write to the windows partition when I tried.

Reality Dunes, always shifting.

---

### Post by logos34 on 2007-12-31
As Paqman said Gutsy comes with the ntfs-3g driver to read/write to windows NTFS partitions, except [you need to enable it with the ntfs-config gui app]("https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971").  Fat32 is an inferior filesystem with several limitations.  

You can read/write to linux ext3 partitions from windows with[ fs-driver]("http://www.fs-driver.org/").

---

### Post by penguinv on 2008-01-07
I still cant partition.

---

### Post by penguinv on 2008-01-08
I still cant partition.
The instructions are given for the earlier than 7.04 Ubuntu screens which are different and give me different choices than what I see.

Isnt it a bug that I get offered for Ubuntu to take up 100% to 49% of my hard drive. 

Read above posts  for details.

---

### Post by radi0j0hn on 2008-01-08
I've had no problem copying and pasting from Ubuntu to my Vista partition.  I have not tried to write directly from an app, as in saving a word processing file, etc. to the Vista area. When I do go to the Vista area, I must giver my password.   John

---

### Post by penguinv on 2008-01-14
I'm the original poster in this thread and I am still wondering and Ubuntu is not on my laptop. 
Here I am trying to attract your interest.

Perhaps I can come at this from a different angle:
[SIZE="3"]
Perhaps there is a standalone formatting tool that will not destroy my Windows XP Pro Partition?[/SIZE]

--since I can't seem to get help to figure out the one in Ubuntu and no one seems to agree with me that the partion manager not allowing me to use less than half of a 40GB HD is a flaw in the ointment. (heh)

I have used fdisk and that was possible on an extended partition but not on a primary partition. (And I never did find out how that worked and what the purpose of it all was.)


-----
I also posted  today  "Re: Cant connect to wired or wireless...."  because on my Averatec, I can't see wireless networks nor connect to one I have the password to. And I don't know what to do. Using LiveCD.

---

### Post by macogw on 2008-01-14
> **penguinv said:**
> I still cant partition.
The instructions are given for the earlier than 7.04 Ubuntu screens which are different and give me different choices than what I see.

Isnt it a bug that I get offered for Ubuntu to take up 100% to 49% of my hard drive. 

Read above posts  for details.

Are you sure it's offering 50-100% of the *whole hard drive*?  I thought that screen asked what % of the free space you wanted to use.

I'd go to System -> Administration -> GNOME Partitioner (I think that's what the LiveCD calls GParted) and use that to resize your Windows partition so that there's 10GB of free space, then create your 1GB and 9GB partitions using it.  After that, start the installer and choose the manual option when you hit partitioning.  Choose the 1GB partition, hit "Edit",  and tell it to "use as" swap and the mount point...that'll either get greyed out or there's a linux-swap option...I forget which.  Hit OK on that.  Click on the 9GB partition and choose "edit" then tell it to "use as" ext3 and the mount point should be just a /  with nothing else next to it.  You can click the Windows partition and tell it to use as NTFS and mount point can be /media/Windows if you like.

---

