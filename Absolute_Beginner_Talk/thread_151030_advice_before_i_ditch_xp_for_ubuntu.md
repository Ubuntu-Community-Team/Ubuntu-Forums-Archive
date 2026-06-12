---
title: "advice before i ditch xp for ubuntu"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by mungy on 2006-03-27
my system has 3 hard drives all ntfs - primary split into 2 partitions 50gb and 25gb, 1 60gb internal and a 300gb external.

there is stuff on all the drives i really need to keep. my plan is to 
1. copy all the stuff i want to keep onto the external drive 
2. delete the partition
3. install ubuntu
4. format other internal drive
5. move the keep stuff to the other internal drive
6 format external drive

is this likely to work? 
can you see any problems i am likely to run into?

thanks in advance :cool:

---

### Post by Sef on 2006-03-27
One problem is that Linux cannot write to NTFS, only read it.  I would make a ext2 partition on your external drive.  XP and Linux can both read and write to ext2.

---

### Post by akiro.yamamoto on 2006-03-27
Actually that seems straight foward.
Although you can do basically the same thing, just use one of the internal HD instead of an external one.
However I would recommend a dual boot scenario until you really become
comfortable with Ubuntu. ;)

---

### Post by meborc on 2006-03-27
[QUOTE=Sef]One problem is that Linux cannot write to NTFS, only read it.  I would make a ext2 partition on your external drive.  XP and Linux can both read and write to ext2.[/QUOTE]
hmm... for that i would suggest fat32... but that's just my thought

---

### Post by Sef on 2006-03-27
> hmm... for that i would suggest fat32... but that's just my thought

If fat32 works, then both are good options, unless there is a reason to use one over the other.

---

### Post by mungy on 2006-03-27
[QUOTE=akiro.yamamoto]Actually that seems straight foward.
Although you can do basically the same thing, just use one of the internal HD instead of an external one.
However I would recommend a dual boot scenario until you really become
comfortable with Ubuntu. ;)[/QUOTE]

i did have a dual boot a few years ago, i think i had mandrake. thats how i come to have 2 partitions on the drive. somehow my mbr died and at the time i had no idea how to fix it, so i formatted and then found out about the control panel booting with win2k cd that would allow me to fix the mbr :D 
i ditched mandrake because i couldn't work out how to install stuff :confused: 

after reading stuff here and playing about with ubuntu live, i reckon i can make it go :-k  after a bit of ](*,)

---

### Post by mungy on 2006-03-27
[QUOTE=Sef]If fat32 works, then both are good options, unless there is a reason to use one over the other.[/QUOTE]

i assumed i would be formatting fat32. i'm still very windows in my mindset, you know part of me just wants to click on things to make them go without understanding what is going on ;) 

another part of me is looking forward to understanding how it all works :cool:

---

### Post by bionnaki on 2006-03-27
the problem with fat32 is the 3 gig filesize limit - any file you might have (movies, isos, etc) that are larger than 3 gig will not be able to be stored.

once you've juggled the files around from one partition to the other, I recommend reformatting the fat32 partition to a "linux filesystem" like ext3 or reiserfs - fat32 is unstable and slow. you'll get good results from using a native filesystem. I prefer reiserfs.

---

### Post by akiro.yamamoto on 2006-03-27
Actually ext3 is a good bet and you can install the Ext File System drivers in windows to enable read and write access to that type of file system.

---

### Post by Sef on 2006-03-27
Both ext3 and reisfers work well.   The only problem with ext3 is that you can get fragmentation in certain conditions as it will set aside a certain amount for a file, but if that file gets bigger then it will place the later parts elsewhere.  E.G., you are doing a dissertation or working on a book or some animation.

---

### Post by xtacocorex on 2006-03-27
Windows can view ext2/3 filesystems with this driver: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

I have yet to try it, but from what I've heard people say on the forums here and around the internet, it seems to work really well.

I would definitely use this if I have to dual boot.

---

### Post by evilc on 2006-03-27
I have Ubuntu on one drive and Winxp on another both seperate to each other(no duel boot), I select which to start from boot via which drive to boot (F11) and have installed Ext2IFS [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) and it works perfect.

---

### Post by catlett on 2006-03-27
Is it a problem to format a 300gb drive any other way than NFTS? I thought that was the main purpose of NTFS, to handle large gigabyte drives. Or does it not matter what file type other than the ability of linux to read/write to it? Just another suggestion, this post [http://www.ubuntuforums.org/showthread.php?t=56723](http://www.ubuntuforums.org/showthread.php?t=56723)  has a different way to install a dual boot than I knew of when I installed. Regards.

---

