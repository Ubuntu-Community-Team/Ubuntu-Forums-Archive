---
title: "Moving MS Office and other files"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Stevo0687 on 2007-03-06
Hey all,
  I think I'm gonna go for it this weekend!! lol  I am finally hoping to set up my computer for a triple book, XP, Vista, and Ubuntu.  My plan is 4 partitions (I have a 120 GB HD).  I want 1 partition for each OS, Ubuntu needs 3 partitions inside itself right? and then a 4th partition to save all my files to that I can access from each OS.  

Currently, I have XP on my laptop.  Dell Inspiron E1405.  I would like to try to keep my XP and not have to reinstall it.  Is that a problem?  I have to delete the backup partition and other system restore partitions, but I've decided to go for it and get rid of them.  If it doesn't work, I have access to XP and Vista install CDs/DVDs and I guess I'll just start over.

What I'm wondering about is my Microsoft Office programs.  I borrowed a legal MS Office 2003 CD from a friend of my g/f and it can only be downloaded so many times.  So I do not want to have to download it again and use up another download.  Is it possible for me move this to the 4th partition so that I can access the programs like Powerpoint and Excel without installing it in each?  Or do I have to just keep it in XP.  Will all my programs have to be installed in each OS or will I install them to the 4th partition?  

My next question is about the files that are currently on XP.  Will I be able to transfer them to the 4th partition w/o putting them on CD?  Will the 4th partition automatically show up in each OS as I install Vista and Ubuntu or is that something I set up?  

I know that was a lot of questions.  Hopefully not too many and hopefully some of you can help.  Thanks in advance.  If you need anymore info about my system let me know.  I'm open to suggestions.  I'm using XP Media Center Edition and will be installing Vista Business and Ubuntu 6.06.  Thanks.

---

### Post by machoo02 on 2007-03-06
Somebody may correct me if I'm wrong, but I don't think it is possible to install applications on a computer so that they are available to multiple versions of an operating system, or at least with MS applications since they will write application/OS-specific entries into the registry.  So, yeah...I think you are stuck installing any MS applications that you want within both XP and Vista.

Ubuntu does not need three partitions...only two are absolutely necessary: / (root) and swap space.  It is recommended to have a separate partition for /home, as it will make backing up personal files easier.

One thing you could do is to set up your 4th partition as ext3, placing your /home partition on this one, and install the [Ext3 file system driver for Windows]("http://www.fs-driver.org/") to be able to access this drive from within Windows (at least XP, not sure if it supports Vista yet, but it seems that most things don't anyway).  Check out [Asiyu's thoughts on partitioning]("http://www.psychocats.net/ubuntu/partitioning").  I have my laptop dual booting XP and Ubuntu, with /home on a separate partition that is mounted as E: in XP, and I moved my "My Documents" folder within windows to be /home/matt, so that the "home" folder in each OS is the same.

Hope this helps some.  Good Luck!

---

### Post by Stevo0687 on 2007-03-06
Thanks!  You answered my main question.  I have a MS Word and a few other MS programs CD that I own.  I mostly wanted to keep the other MS office programs because I sometimes need Excel and Powerpoint for college.  If I can keep my XP and not have to start all over with installing it, I don't mind just booting to XP when I need to use Excel or Power Point.  Thats not a big deal.

Now I'm just wondering how I move my documents from XP to the 4th partition.  Like my iTunes and stuff like that.  So that I can access them from an OS.  

I'll read up on the other links you posted.  Thanks again!  Any other advice or info by anyone is greatly appreciated.

---

### Post by AndyCooll on 2007-03-06
For dual-booting queries see the link in my signature.

About MS Office. Have you tried Openoffice? It will run most Powerpoint and Excel files (and files can be saved in these formats too if required).
And about your 4th partition query. To run MS Office you'll need it to be on a partition with an OS! You can store a copy of it on your 4th partition, however it won't run. Without being properly installed it's like keeping a copy of the CD itself, useless until actually installed on to an OS.

:cool:

---

### Post by mac.ryan on 2007-03-06
> **Stevo0687 said:**
> Ubuntu needs 3 partitions inside itself right?

i am not sure I got your question. From what you wrote, I would suggest you have an EXT3 partition (10 Gb or more) for installing ubuntu plus a swap partition (typically double the size of your RAM, unless you have very large amount of RAM). So: 2 partitions to set up your ubuntu.

> Currently, I have XP on my laptop.  Dell Inspiron E1405.  I would like to try to keep my XP and not have to reinstall it.  Is that a problem? Normally no, unless some unusual problems (I did it a certain number of times and never had problems).

> Will all my programs have to be installed in each OS or will I install them to the 4th partition?For most of the things, you will have to install them twice, once for each of the two Micro$oft systems. You might try to install window$ programs on linux through something called "wine", but this is like going in a vegetarian restaurant and trying to get a steak... if you go to a vegetarian restaurant... well, try vegetarian food instead, use free software instead! :)

> My next question is about the files that are currently on XP.  Will I be able to transfer them to the 4th partition w/o putting them on CD?  Will the 4th partition automatically show up in each OS as I install Vista and Ubuntu or is that something I set up?The easiest way is to format your data partition in FAT32: in this way all the systems will be able to read and write on that partition. You can do that also with NTFS partitions, but it is slightly more tricky, implies some risks, and doesn't get all functionalities.

You will be able to transfer all your files without passing through CDs. All the system will recognise the data partition without problems.

> I'm using XP Media Center Edition and will be installing Vista Business and Ubuntu 6.06.  Thanks.If there is no specific reason to install the 6.06 version of ubuntu, I would suggest to install the 6.10 (edgy eft) instead.

A final comment: if your Dell has the media direct key, then either you give up on that functionality, either you will have to install ubuntu in a non-standard way. In fact GRUB (the program that allows you to select what operating system you want to boot your computer with) breaks MediaDirect, and vice versa.

Hope this helps at least a bit,
Mac.

---

### Post by Stevo0687 on 2007-03-06
Alright!! Thank you very much everyone.   Many great responses!  AndyCooll, I was definately hoping to look into that.  But I guess I'll have MS office on XP if I do ever need that specifically. 

Mac, I'll have to read over your post again, it was a lot of great info.  I was just planning on 6.06 because I already have the install CD.  Is 6.10 the latest available online?  I guess I could go with that just as easily. 

About installing MS programs through wine, I may try to tackle that someday, once I get more used to it, but for now, when I was talking about using MS programs, I just meant on XP and Vista, not Ubuntu.  I'll play around with each slowly as I get used to them, but nothing big for now.  Just the basics and keeping XP going and getting Vista better so that I can use that as my main Windows.



I do not know what the media direct key is.  What is it?  How do I find out what it is and if I have it?  And what would I be giving up?  

Are you saying I will give that up OR I'd have to install Ubuntu differently?  Or that if I have it I will have to to install it differently, and I will lose functionality either way?  


Thats all the questions and comments I have for now.  I'll have to read through these posts a few more times and make sure I understand everything.  Thanks again so much for the quick and very helpful replies!

---

### Post by mac.ryan on 2007-03-06
> **Stevo0687 said:**
> Mac, I'll have to read over your post again, it was a lot of great info.  I was just planning on 6.06 because I already have the install CD.  Is 6.10 the latest available online?  I guess I could go with that just as easily.

Yes, Edgy is the latest stable, there are lots of great improvements at any ubuntu release, so - unless you are a big corporation that prefers seldom changes over best features - I would strongly recommend to regularly update your system to the latest version (the next being scheduled for April 2007).

> I do not know what the media direct key is.  What is it?  How do I find out what it is and if I have it?  And what would I be giving up?It is a button on your keyboard, with a house on it (so, if you had, you would know by now! ;) ). It launches a windows-based very light OS, that allows you to get playing music, videos, and see docs, without having to boot the entire Windows (XP or Vista).

---

### Post by Stevo0687 on 2007-03-06
HAHA!  I do have it!  But obviously I don't use it so I guess thats not a big deal.   I'll give up one button for a whole 'nother OS! lol  I'll still have the Media Center features, correct?  Just not the use of that button?  And all my other volume, pause, play, buttons and such will be fine also, right?  

I guess I'll go with 6.10, also.  Sounds like a good idea.

I'm a college student so I've already taken a lot of studying time posting all this. lol  So I'll try to get what reseach I can done this week and hopefully try to tackle this, this weekend.  But we'll see.  I don't want to rush and mess anything up.

Also, I guess I should not, I was planning on using a GParted CD that I have to delete my other partitions and such and then install Vista I belive and Ubuntu last, if I'm correct on what I've heard is the best order.

Thanks again for all your help Mac and everyone.

---

### Post by mac.ryan on 2007-03-07
> **Stevo0687 said:**
> I'll still have the Media Center features, correct?

I am not a Window$ user, but yes, removing the DirectMedia do not affect the main windows installation.

> And all my other volume, pause, play, buttons and such will be fine also, right?

Not only fine, but because they give standard keyboard inputs to the bus, other systems will be able to use them as well. I have a DELL XPS M1710 and they work fine in Ubuntu, for example.

> I was planning on using a GParted CD that I have to delete my other partitions and such and then install Vista I belive and Ubuntu last, if I'm correct on what I've heard is the best order.

Yes, ubuntu must come the last, as installation of any Window$ system will bulldoze grub (the small prog giving you the choice of what OS to boot).

> Thanks again for all your help Mac and everyone.

We help you, somebody else helped us... ;)

---

### Post by Stevo0687 on 2007-03-08
Alright, just a few questions here.  I'd say a few last questions, but I know that won't be the case. lol

For Ubuntu, I think I'm gonna try to do the /home "partition also, along with the main Ubuntu partition and the swap. Can these 3 be inside one primary partition?  

Also, I have 1 GB memory.  Do I really need a 2 GB swap?  From what I've read I probably don't.  Will 1 GB be enough? What do you all suggest?

Alright, I have XP shrunk to the size I need it.  (I did that back in December when I thought I'd do this the first time, but at the time didn't know if I was willing to sacrafice my backup drive and restore capabilities).  Anyway.  once I delete the other partitions and just have XP.  Should I install Vista on the rest and worry about creating a partition for my documents and other data later when I add Ubuntu, or should I add the shared data partition and make Vista the rest and then let Ubuntu shrink Vista when I install Ubuntu, or should I create all the partitions to the sizes I want them ahead of time?  (I hope you can follow all that. lol)

I'm guessing I may want to shrink down my XP partition after I transfer my documents and such to the shared partition.  Will I be able to add that space on the hard drive to my shared data partition later?

Alright, I think thats the questions that I have for now.  I may try to start some of this tomorrow.  We'll see.  I've got a big test tomorrow and Monday so I have  a lot of studying, but I hope to make time.  Thanks again in advance.

---

### Post by mac.ryan on 2007-03-09
Hi Stevo,

> **Stevo0687 said:**
> For Ubuntu, I think I'm gonna try to do the /home "partition also, along with the main Ubuntu partition and the swap. Can these 3 be inside one primary partition?

I guess not. AFAIK, primary partitions are the only bootable and can't be divided in logical drives (you can do that only with extended ones). So I would suggest a partitioning scheme like this:[LIST]
[*]**xp** - primary
[*]**vista** - primary
[*]**ubuntu** - primary
[*]extended partition:[LIST]
[*]**swap**
[*]**data**[/LIST] [/LIST]Anyhow, as I never tried to split a primary partition into bits, you can just try yourself and see what will happen (or somebody else who tried can share his/her experience in this thread). I guess the worst it can happen is the programme refusing to do it... :o

> Also, I have 1 GB memory.  Do I really need a 2 GB swap?  From what I've read I probably don't.  Will 1 GB be enough? What do you all suggest?I don't have direct experience with that configuration. I have to say that with 2 Gb of RAM, my swap partition (2 Gb too) is hardly ever used.

> Once I delete the other partitions and just have XP.  Should I install Vista on the rest and worry about creating a partition for my documents and other data later when I add Ubuntu, or should I add the shared data partition and make Vista the rest and then let Ubuntu shrink Vista when I install Ubuntu, or should I create all the partitions to the sizes I want them ahead of time?  (I hope you can follow all that. lol)If you know how big you need your partitions beforehand, partitioning first and installing afterwards makes everything much easier (and safer).

> I'm guessing I may want to shrink down my XP partition after I transfer my documents and such to the shared partition.  Will I be able to add that space on the hard drive to my shared data partition later?AFAIK, you can only append space to partitions (i.e. adding it at the end of them, and not at the beginning). The same for shrinking a partition: it can only be "cut" at the end of it, not at the beginning. Unless I am wrong with what above, this means that it might be tricky to "pass" the space from one partition to the other. If you have to go from situation 1 to situation 2:

```

CCCCCCCDDD (starting situation)
CCCDDDDDDD (final situation)
```

I imagine you only option is to: cut partition C, create a partition E in the middle, transfering data from D to E, removing D, extending E. In graphical terms:

```

CCCCCCCDDD (starting situation)
CCC----DDD (data transfered to D and resized C)
CCCEEEEDDD (new partition in the middle)
CCCEEEE--- (data tranferred from D to E)
CCCEEEEEEE (E has been extended)
```

What above implies you have enough space on the "DDD" to host all your data at once AND that I am right in assuming you can change size of partitions only moving their end point (can anybody confirm this?).

Best luck with the test! ;)

---

### Post by Stevo0687 on 2007-03-09
Alright, thanks.  I think I understood most of that. lol  I'll pop in my G-parted CD this afternoon and do some deleting and such and see how it goes.  As long as I don't hurt my XP partion, which I don' t think I need to touch right now, then I'll be fine.  If I mess anything up with Vista or Ubuntu I can just start over.  I think I'll try to figure out my partitioning sizes ahead of time and preestabish them.  Thanks again for the help. We'll see how it goes.

---

### Post by Stevo0687 on 2007-03-09
Alright, I came a cross another problem.  One of my partitions is, utility with diagnostics to test the hard drive.  That is what I was told by Dell.  Do I need this?  It is a Fat 16 file system, I think I've tried to move that to the XP partition before and it wouldn't work.  How do I handle this?   Can I include it in any of my partitions or do I need it at all?  The sooner I get a response on this one, the better.  Thanks.

---

### Post by Stevo0687 on 2007-03-09
Another question...now that I'm sitting here trying to do this all the other questions pop up.  

What size should I make the Vista partition?  I saw somewhere about 15 GB minimum.  I mean I won't be storing files on it, thats what the shared partition is for, I'll just have the OS itself and programs that I add to it correct?  Will 15 or 20 GB be ok?

---

### Post by mac.ryan on 2007-03-09
Hi,

for the FAT16 partition, I have no clue. What I did on my dell when it was shipped to me was to erase the HD completely and reinstall everything from the scratch (I am telling this, because I assume if my computer works well, that partition is probably unnecessary). There is a good chance your FAT16 partition is the one hosting the "MediaDirect" mini operating system, though.

My experience with "recovery utilities" (an an Acer TravelMate) were more a disaster than an help, as they were erasing completely the HD (including other OS and reinstalling windows and the boundle progs...).

As for the minimum Vista requirement, I have no clue. I think the best would be to goole it on some Vista-fans forum! ;)

Have fun with your ubuntu installation!! :)

---

### Post by Stevo0687 on 2007-03-09
Alright, sounds good.  I'll delete it. lol  From what I read on it, I think if I have to I can get the program that is in it from online.  And like you said, you deleted yours completely and you're fine so I'm not worried.  I'll either be up late tonight fooling with it or I'll start it tomorrow. Thanks again.  I'll probably be posting more questions as I get going. lol  So check back. lol Thanks.

---

### Post by Stevo0687 on 2007-03-09
I think I'll start a new thread for my dell partition problems.  The topic doesn't pertain to my questions now, and I'd like as much help as possible.

---

### Post by Stevo0687 on 2007-03-09
Continued here...[http://www.ubuntuforums.org/showthread.php?p=2274489#post2274489](http://www.ubuntuforums.org/showthread.php?p=2274489#post2274489)

---

