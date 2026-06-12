---
title: "Actually initially installing Ubuntu with a million questions"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Invictious on 2007-02-12
Hello everyone, might as well make my first post here.
I have had plenty of programming experience, mainly in Java. I am 15, and I live in Hong Kong. I am NOT a nerd, and I focus on internet and computer security (my friends make things, and I break things :popcorn: )
I also have had plenty of forum experience, so no need to brief me on the basics.

Let's cut the junk, and get straight to the point.

I have Ubuntu CDs coming in a few weeks, already before they come, I realize a major problem.
here are my specs
1) one hard drive
2) 2 NTFS Partitions (both are used)
3) No more space on hard drive for another partition.

Already, there goes the installation problem. Where can i install it? There is no room for another partition, and I cannot buy another hard drive.

How would I install Ubuntu onto an existing partition? If I can use the existing D Partition, that would be great. Problem: How do i move everything in D partition to C partition, and can I just install ubuntu over D partition?

If that's the case, can I make it dual boot on startup?
I also use OO suite already, so I presume it should be compatible between windows and Uubuntu?

I have heard of UNIX OS's for a long time, and finally it's a time to install it. However, when should I use Ubuntu and when should I use Windows? Obviously Windows for Gaming and Ubuntu for other purposes. A question here is how can I switch between Windows and Ubuntu quickly and efficiently?

Thanks for people who answers most of the questions and actually took their time to read it.

---

### Post by renzokuken on 2007-02-12
my advice would be to boot into windows, copy everything from the D: partition to your C: partition. (or burn it to CD if no room).

make sure you leaving the parttion that windows is actually installed on (usually C:) alone, not deleting that one.

boot the ubuntu cd, select to install to the D: partition. let the installer finish.

ubuntu will automatically install GRUB, a bootloader, that lets you choose whether to boot into Windows or Ubuntu on restart (a dual boot)

Open Office comes as part of ubuntu so it is installed already, and there should be no compatability problems with the windows version.

---

### Post by Bachstelze on 2007-02-12
You could for example move all data from the second partition to the first one in Windows, then the Ubuntu installation program will let you delete it and create partitions for Ubuntu instead.

Another approach, if you have enough free space on either partition, would be to shrink it and then create your Ubuntu partition in the free space created that way.

n both cases, you can do a dual boot. The only way to switch between the two OSes will be to reboot the machine.

Hope that helps :)

---

### Post by Invictious on 2007-02-12
If I remember correctly, resizing NTFS Partition = Deletion of All Data in that Partition.

So I just open up D Partition, Ctrl A then Ctrl X and Ctrl V onto C drive, and then I am set to install Ubuntu?

According to what I know, if i cut everything and past onto C drive, ALOT of things won't work. E.g. Windows will NOT boot. I know this because I tried it before.
Ouch, painful memories.

---

### Post by renzokuken on 2007-02-12
may need some more info

what are the letters of your partitions?
which one has windows installed to it, and what is the other partition used for (what files on it?)?
what are the sizes and amounts of free space of the two partitions?

---

### Post by Henry Rayker on 2007-02-12
It will depend on what sorts of things are on your D: drive. If you have apps and stuff installed over there, you'll be in a bit more trouble. However, if D is just data, you won't have an issue.

Some computers come pre-installed with a D: drive being a backup drive or something like that...not sure how to proceed if that is similar to your case. I guess we just need more information about your computer setup, most importantly, what's on your C: and what's on your D: drive.

Resizing an NTFS is usually only bad if you don't defrag the crap out of it first (at least 2 times). I've resized many times and had nothing go wrong..

---

### Post by Bachstelze on 2007-02-12
> **Invictious said:**
> If I remember correctly, resizing NTFS Partition = Deletion of All Data in that Partition.

Wrong. You can very well resize a NTFS partition without losing all your data, I've done it countless times. YOu still should backup your important data just in case but the risks are very low.

---

### Post by renzokuken on 2007-02-12
before resizing ntfs though i would highly recommend defragging it first

---

### Post by Invictious on 2007-02-12
Of course, will the bootloader provide an option to resize the partitions?
Oh yes, when I am using Ubuntu, am I only limited to the partition that I have?

Well in C drive, there is the usual program files and windows.
in D drive, there are a few drivers installed. There is also WUTemp and Temp.
more importantly, my documents.

C Drive is 39 gigs. Useable space of 26.1 gigs
D Drive is 37.2 gigs. Useable space of 17.6 gigs

I have like..300 megs left for another partition?

I think I also might have an app or two installed over at D.

Gah, if I could just buy a new harddrive and get it all over with.

---

### Post by tonyr1988 on 2007-02-12
The bootloader (GRUB) allows you to choose which partition to boot into at startup.

The option to resize partitions will come in the partitionar (GParted) that is on the installation CD. And yes, it will allow you to resize NTFS partitions.

No, you're not limited to only the one partition. It can read/write from ext*, NTFS (limited beta support...it's reverse-engineered), FAT*, ResierFS, and many others.

If you have a lot of data, you may want to have three partitions:

NTFS - Windows
FAT32 - Data (Music, Documents, Videos, Pictures, etc.)
EXT3 - Ubuntu

That way Windows and Ubuntu can share data easily without having to look at each other's operating system partitions.

---

### Post by CujoQuarrel on 2007-02-12
1) Move everything that you want to keep to drive C:
2) Go back and check for the things you forgot :-)
3) Then do the install.

With the standard install GRUB will let you boot to either OS. From Linux you can read the NTFS partition and there are beta drivers that let you write. I have heard that there is some way to get XP to read/write ext3(2?) partitions but I've never looked in to it.

You might try the path that I am heading down instead of a dual boot machine. Use XP in a virtual machine so that you don't have to reboot to get to XP , just run it in a window. Trying out VirtualBox for this.

---

### Post by Invictious on 2007-02-13
NTFS for solo windows.
FAT32 for sharing data between the two OS since it's accessible between the two OS'es.
and EXT3 is the only thing that Linux.

Seems like a good idea, but if I changed the partition where I contained all the data, something bad seemed to happen. e.g. I have to format the partition or something along the lines.

I am rather new to installing something like this, and the partitions give me a headache. Why do people make life so difficult?

---

### Post by tonyr1988 on 2007-02-13
Yes, if you change the filesystem of a partition, it must be wiped.

If you just resize a partition, you shouldn't lose your data (I've never had problems, but defrag / backup important stuff first!).

If you've been running Windows on one computer for a while and it's taken over all your hard drive, it can be a pain. Unfortunately, this isn't a Linux issue - if it was the other way around (planning for installing WinXP), it would be a lot worse.

---

### Post by Invictious on 2007-02-13
Oh well, then I will just resize my D Partition
and some of C partition, so I will get some free space.

I will keep everything Linux based onto one partition itself. Well looks like I just have to wait for a month.

While then I will just get myself familiar with Linux, and think of more questions.

---

