---
title: "Windows Media/WINE/Partitioning Questions"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by pink_taco on 2006-07-27
Hello all,
First off, I am currently running Dapper Drake on a dual-boot system alongside Windows XP Media Center Edition.  I got my laptop from a friend of mine.  When I got it and reloaded XP, The drive was already partitioned because he had a Linux Installation on there previously.  The hard drive's capacity is roughly 74 GB.  The partitions that existed when I got the computer were something like a 60GB/14GB ratio.  Of course, XP was installed on the 60 GB partiton and the 14 GB partition was just listed as a blank drive within XP.  So, havinig no Linux on the computer and wanting to get into it myself, I installed Ubuntu.  I let the Ubuntu installer do the partitioning for me and I sorta messed it up.  The OS works and all, don't get me wrong there, but what I'm trying to say is that when I used the automatic partitioning tool, It partitioned the 60 GB portion and left the 14 GB partition alone.  So, after this, the 60 GB partiton had now been cut down to 51 GB and Linux  was installed on 9GB.   ;)   I hope I'm not being too confusing.  Just to clarify, at this time, I've got a 51 GB partition w/ XP Media Center Installed, a 9 GB partition with Ubuntu installed, a swap partiton (i'm not sure how big it is...  a few hundred MB's i'm sure), and of course, the empty 14 GB partition that's viewable from Windows.
It's my goal to make Ubuntu my primary OS, and still have the XP installation but with less space allocated to XP and more space allocated to Ubuntu.  I've got roughly 23 GB or .wma files on the XP partition as well and that really is my main concern.  I've been reading up on WINE and all, but I'm still confused.  I'd like to have a bigger Linux partition and use that primarily, but still be able to have all of those .wma files organized in the same heirarchy that they already are.  I really don't want to lose my media library.  I can use the audio converter within XP media center edition to convert them to .mp3 files with a smaller bitrate if playing .wma's in Ubuntu is too difficult.  I understand that WINE can run Windows media player, but I don't really know too much about it.  Is it possible to run Windows Media Player within WINE and have it read the data from the existing XP partition and listen to my media library that way?  I really want to make the switch, I just dont' want to lose all of my ripped. audio.  I could move the entire library to another computer's drive if there was an existing Linux program that would let me just copy what was essentially the contents of the windows "my music" folder into some other folder.  Could someone give me some good advice?  I'm sorry if this was long-winded, or hard to understand.  Any help is greatly appreciated!  :D

---

### Post by ovimunt on 2006-07-27
Right... let's try to keep things simple for a minute... :D 

Easiest way would be to use something like Partition Magic to get rid of all those random partitions except the Windows one. Before I go any further please let me know if you have/know about this software, Partition Magic.

Also, you don't need wine AT ALL! In Ubuntu you already have ALL the software you need to play any sort of audio/video file. As for your media library I'm sure there is some way to import it into a linux native player.

So, first of all, do you have Partition Magic?

---

### Post by pink_taco on 2006-07-27
I have heard of the program and seen evaluation versions that don't really function unless you make a purchase.  In short, no, I don't have Partition Magic  :sad:

---

