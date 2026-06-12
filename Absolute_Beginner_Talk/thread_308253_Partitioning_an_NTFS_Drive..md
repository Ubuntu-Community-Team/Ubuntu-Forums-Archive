---
title: "Partitioning an NTFS Drive."
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by cutlerite on 2006-11-27
After reading many of the previous posts regarding partitioning HD's, I have come to the conclusion, that I know nothing about partitioning.

I was told that the Ubuntu installation cd would guide me in creating a new partition, **However-** The partition guide locked up, and didn't go anywhere.  

After trying to research what is going wrong, I realized it is difficult to partition NTFS drives?  

So here's my situation.  I need to partition my hd in **windows** first, then install linux.  (I think that's how it should be done).  I don't believe NTFS-3g runs on windows, because I downloaded it, and I have no idea how to get it going on windows?

I know this is probably the most horrible of the absolute beginner talks.  But I really need someone to just walk me through this whole partition hoop.

I only have one hard drive.  I'm running a AMD athlon 64 processor, 1024mb of DDR SDRAM, 250GB 7200RPM serial ATA hard drive.

help? can someone just IM me? Trentcutler

---

### Post by taurus on 2006-11-27
This website will walk you through the whole process...

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by turbojugend_gr on 2006-11-27
My view on the topic: Ubuntu LiveCD uses Gparted to make things happen and it semms easy to follow to me, both now and back when I was a first-timer.

You just tell tha partitioner what yu need (wheteher that is taking a whole drive, or creating some space for it,) anyway I 'll pm you asap.

---

### Post by bodhi.zazen on 2006-11-27
> **cutlerite said:**
> After reading many of the previous posts regarding partitioning HD's, I have come to the conclusion, that I know nothing about partitioning.

LOL :lol: see here: [Basic partitioning](http://ubuntuforums.org/showthread.php?t=282018)

> I was told that the Ubuntu installation cd would guide me in creating a new partition, **However-** The partition guide locked up, and didn't go anywhere.  

After trying to research what is going wrong, I realized it is difficult to partition NTFS drives?

So here's my situation.  I need to partition my hd in **windows** first, then install linux.  (I think that's how it should be done).  I don't believe NTFS-3g runs on windows, because I downloaded it, and I have no idea how to get it going on windows?

I know this is probably the most horrible of the absolute beginner talks.  But I really need someone to just walk me through this whole partition hoop.

I only have one hard drive.  I'm running a AMD athlon 64 processor, 1024mb of DDR SDRAM, 250GB 7200RPM serial ATA hard drive.

help? can someone just IM me? Trentcutler

LOL :lol:

Yes it is overwhelming at first.

Start in windows. Defragment your HD. Twice for good measure ! BACKUP YOUR DATA.

Next, boot the Ubuntu CD, start gparted, RESIZE the NTFS partition.

Install Ubuntu into the free space, choose automatic partitioning.

[Illistrated install guide](http://www.psychocats.net/ubuntu/installing)

viola!

enjoy !

---

### Post by shin on 2006-11-27
If I understood correctly, you got windows installed on some ntfs partition which you want to resize and create another partition for linux. I highly doubt that Ubuntu installer handles resizing ntfs partitions. Do that while in windows - with partition magic or something (I think there is some freeware software for this). After resizing, do not create a new partition, just leave unallocated space.

Now start ubuntu installation and use this unallocated space - I recommend using jfs filesystem instead of default ext3 (you can change it in advanced mode). One more thing if you will use advanced mode - be sure to create 2 new partitions in ubuntu installation - one should be swap (FS swap, size about 2x size of your RAM) and use the rest of unallocated space for root partition. 

Dont modify your existing partitions (windows etc), but you may set mountpoint for them during installation. This way after installation your windows partition should be visible but accessible in readonly mode. To change that - install ntfs-3g and change 'ntfs' word in /etc/fstab to 'ntfs-3g'.

There is no ntfs-3g for windows. Why should be? It is a driver to actually access ntfs partitions with read/write access. And windows already got that feature (at least xp/nt/2003 etc, but who cares about 9x these days).

---

### Post by bodhi.zazen on 2006-11-27
> **shin said:**
> I highly doubt that Ubuntu installer handles resizing ntfs partitions.

Hard to believe, but true :p
[indent]via gparted ;)[/indent]

---

### Post by shin on 2006-11-27
> **bodhi.zazen said:**
> Hard to believe, but true :p
[indent]via gparted ;)[/indent]

Whoah, didnt know that ;) Ntfs always seemed to be the least supported filesystem in linux of all. Finally things has changed :cool:

---

### Post by bodhi.zazen on 2006-11-27
> **shin said:**
> Whoah, didnt know that ;) Ntfs always seemed to be the least supported filesystem in linux of all. Finally things has changed :cool:

Check out [ntfs-3g](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by cutlerite on 2006-11-27
even attempting to do it manually, it still says file system error. 

I think the Defrag might be a good idea, because apparently Compaq (the computer manufacturer) is somehow preventing me from putting something other than windows on it.  or there is just an error on the drive, which doesn't make sense because I bought the computer friday.

a guy from the forums is helping me via AIM right now, but we're still getting errors.

---

### Post by 56phil on 2006-11-27
How much free space is on your windows partition? A good healthy defrag can't hurt, but if yoy don't have the free space gparted won't be able to resize that ntfs partition to make space for Ubuntu. Good luck.

---

### Post by jdong on 2006-11-27
Tips that I can give you:

 * Ubuntu's installer does indeed support partitioning and safely resizing NTFS out of the box, but it might not have the highest success rate.
 - To prevent from scaring you, by "success rate" I mean whether or not it'll allow you to resize. The Linux NTFS tools have lots of built-in safety checks so that it only begins its work if it is confident that it'll be able to successfully finish it. In my 50+ NTFS drives I've resized before using Ubuntu, I only recall 1 or 2 that didn't go through (because of fragmentation), and no data was lost -- the program just refused to do the resize.
 * Ubuntu's NTFS resize tools are not the most up-to-date. The newer versions are more capable of dealing with fragmentation and bad blocks. They are usually included on the most recent releases of the GPartEd LiveCD ([http://gparted.sourceforge.net/livecd.php)](http://gparted.sourceforge.net/livecd.php)). Try that if the Ubuntu LiveCD gives you a hard time. It's the exact same partitioning program, but with newer versions of the partitioning tools


If worst comes to worst and the Linux utilities for resizing don't work on your system, your last option is to use a commercial tool like Partition Magic to do the resize.

---

### Post by cutlerite on 2006-11-27
> **56phil said:**
> How much free space is on your windows partition? A good healthy defrag can't hurt, but if yoy don't have the free space gparted won't be able to resize that ntfs partition to make space for Ubuntu. Good luck.

its a brand new computer, I have about 206 gigs free.

---

### Post by cutlerite on 2006-11-28
Okay, I'm just going to post to this thread again, in case anyone has similar problems.  The new Compaq computers might have a block from partitioning a hard drive, installed in their "recovery" portion of the new hard drive.

I was having major issues trying to install ubuntu, because it wouldn't go anywhere.  So I went back into windows, defragged, and then did a "check hard drive" which is an option when you right click on the hard drive and view drive properties. 

This solved my original issue, but it may not solve other peoples, Because I know other people have had the same issue.  

You may need to go into the windows recovery console, and fix the MBR (master boot record).  There is a software application that can do that for you, but I am unfamiliar on how it works.  

If you are having the same problem as I did, defrag, and check the hard drive a couple times, and it will somehow, miraculously come around.

---

### Post by bodhi.zazen on 2006-11-28
My guess is you were having problems with fragmentation...

---

### Post by louieb on 2006-11-28
There is regular poster here named Herman. This is his web site.  Its all about duel booting.  [URL="http://users.bigpond.net.au/hermanzone/"]Illustrated Dual Boot Site
[/URL] or since I have not seen it mentioned here yet the  [Psycho Kitties]("http://www.psychocats.net/ubuntu/index.php") site. She knows Ubuntu.

---

