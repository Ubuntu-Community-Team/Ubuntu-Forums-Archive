---
title: "questions about partitioning"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by dckirba on 2006-04-21
Hello All,

I am very new to all this which is why I'm on this forum I guess :) I just ordered a bunch of CDs from Shipit and while I'm waiting for them to arrive, thought I'd do a little research. I run Windows Xp and have an 80 Gig HD partitioned into 10,30 and 40 gig. I am getting another 80 Gig HD and an additional 1 Gig of RAM because prices just dropped for some reason this month :) Now my question is - When i install Ubuntu, will I be able to install it onto my second empty HD without doing any partitioning? Please remember, I have never done any of this before. I would like to have a dual-boot. I did read a lot of stuff before I came here, but I didn't find anything anywhere about multiple HDs, just partitioning an existing one. 

Also, I live on dialup and I just read the 'Is Ubuntu for you' thread. Does it really take forever to download everything I'd need? Would leaving my machine on for a night do the trick? :confused: 

Sorry for all the questions. Thanks in advance,

Cheers,
David K

---

### Post by Charax on 2006-04-21
well, Ubuntu automatically creates at least two partitions - Root (for all the OS files) and Swap (it uses a swap partition instead of a swap file) - this will happen for the most part without any need for you to control it. However, most people (from what I've seen) create at least one extra partition for /Home (personal files for all users) - this helps when backing up data (as you can just copy the /home partition) and reinstalling (as you can wipe /root without losing your personal files)

Personally, I have 4 partitions - /home, /root, Swap and /tmp - I found I had problems using Wine if /tmp was on the /root partition.

Ultimately, the complexity of your partitioning system is up to you, but Ubuntu will always have 2 - /root (min size 1.5 Gb) and Swap (min size 256MB)

EDIT: Yes, it takes ages - not so much because of big files, but because of the number of them - whenever I use apt-get update/upgrade on a fresh install it generally takes about an hour, but only about half of that is downloading files. A good aspect of the Linux system is that you can get away with downloading small groups of packages instead of the whole lot at once.

---

### Post by tonyr on 2006-04-21
The short answer is yes, you can install Ubuntu on the second drive without doing any
partitioning.  

In reality it's not quite that simple.The installation process will figure out what's what
hardware configuration-wise and ask you what you want to do, where you want to install
Ubuntu.  I think the default is to make a single partition out of the unused space on
the drive you choose.

---

### Post by AndyCooll on 2006-04-21
> When i install Ubuntu, will I be able to install it onto my second empty HD without doing any partitioning?

Yes, sort of. It should automatically detect your second drive, however the install default option at the partitioning section is to wipe the lot, so you'll probably just have to change that option to "use the free space ..."

> Also, I live on dialup and I just read the 'Is Ubuntu for you' thread. Does it really take forever to download everything I'd need? Would leaving my machine on for a night do the trick? :confused:

Yes it might well take a long time, though it depends on what you want to install. You might decide not to install any additional software at all (that's up to you). Typically however, just to download updates is a good few hundred mb's. So, yes again, leaving your box on overnight might well be what is required.

:cool:

---

### Post by catlett on 2006-04-21
When you put in the install disc and turn on your computer it will boot if your computer is setup to boot to the cdrom drive(You check this in your bios. If you don't already know about this just Google bios settings for cdrom).
When the disk boots and runs just hit enter. It will take you through some hardware detection and then to the partitioner.
Here is where you will choose to put the install on the second hard drive. The partitioner will give you options.(It might not be like this word for word but you'll get the idea)
"Erase ide drive maxtor master 80 gb and use entire disk for install"
"Erase ide drive WD slave 80 gb and use entire disk for install"
It will list all your drives and ask if you want to erase one and use it. If you have a flash drive or memory card in it will give you those as options. Just be sure to know the brand of your drive and it's size as well as which one is master and slave.
Just highlight the disk you want to put Ubuntu on and hit enter. The install will format and partition it for Ubuntu. Ubuntu is heavily reliant on an internet connection for install and updating. If you choose all the defaults I think you'll be downloading over 1gb of data. The disk has around 600mb(I think) and the install ends up over 1.5gb(These are guesstimates I don't know the exact numbers). The difference between the cd and install is loaded by internet connection.

---

### Post by dckirba on 2006-04-22
Thanks a lot guys. That does answer most of my questions. I will most probably have a lot more once I actually get the disc and start installing :)

Cheers
David K

---

### Post by morequarky on 2006-04-23
[QUOTE=Charax]
Personally, I have 4 partitions - /home, /root, Swap and /tmp - I found I had problems using Wine if /tmp was on the /root partition.
[/QUOTE]

partitioning in ubuntu gives me options on setting up different folders of linux in different partitions like the above statement.

I tried creating many partitions on my system for each type and it won't let me create but a few and then it says the rest of my harddrive is unusable.(breezy)

What are the different folders for?  how large should they be if i make them into a partition?  I have many questions about this kind of partitioning and haven't found a howto on it explaining the differences and why it would be useful to have them.  The quote above is the first time i heard of a reason to use '/tmp' in it's own partition.

Can someone explain this kind of partitioning to me?

quarky

---

### Post by tonyr on 2006-04-25
The partitioning issues are mainly risk, data volume management, and convenience.
Using several partitions reduces the risk that damage to any one partition will make
all (or other) data inaccessible. It allows for the separtation of fairly stable sets of
files/programs from highly changeable files/programs.  It means that backups, if you
are doing them, can be faster for smaller partitions and can be ordered and sheduled
in terms of priority and criticality.  

These and other partitioning topics are covered in some detail in these documents:
[URL="http://www.debian.org/releases/woody/i386/ch-partitioning.en.html#s4.4"]
http://www.debian.org/releases/woody/i386/ch-partitioning.en.html#s4.4[/URL]
[http://www.tldp.org/HOWTO/Partition/]("http://www.tldp.org/HOWTO/Partition/")

---

