---
title: "Should I Just Get Rid Of Windows?"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by Seldoms on 2006-08-17
I only have a 32 gb drive. I have 21.74 free. I would like opinions on rather to just get rid of windows and go to ubuntu, or opinions on how I should partition my drive.

I think I would play big games (WoW) on Windows and relax on Ubuntu, it is much more user friendly.

I am new to linux/partioning so if someone could tell me how to partition, what do do I would be very grateful.

Its really weird. I've been windows all my life and I dont know whether to switch or not. >.<

---

### Post by GeekSpeek'r on 2006-08-17
Not necessarily. I would download vmware server, install, and then install/run ubuntu in windows to see if you really like it. Windows has its plusses, but ubuntu can really meet those if you just try and are willing to learn something new.

---

### Post by az_human on 2006-08-17
As long as you back up all of the data that you need that currently resides on your Windows partition(s), then go ahead!  If all else fails (and it oftentimes does, so don't feel bad), then you can reinstall Windows for a bit.

I found myself switching back and forth between Windows and Linux a LOT.  I was, of course, most comfortable in Windows.  Linux was very enticing, though, so I would swap over.  Be prepared for the learning curve.  When it gets too overwhelming, you'll have the urge to go back to Windows.  Don't hesitate to do that -- because you'll come back to Linux once again and things will make that much more sense to you when you're back.

I can't count how many times I've been back and forth, but I am COMFORTABLY using Ubuntu now.

---

### Post by wapowell on 2006-08-17
Hi,

I would say that this is a decision that is a personal one to you.  Meaning, you will hear opinions on this board that will tell you to do one thing or the other but in the end you have to do what you are more comfortable with.

I'll try to answer your post in points.

About partitioning...  I did the same thing as you (pretty much).  I had Windows XP and wanted to try Ubuntu back in the warty days.  At that time (haven't tried since) the Ubuntu installer didn't support nondestructive resizing of a NTFS partition.  I am not sure if the dapper installer allows for nondestructive resizing of a NTFS partition.  The tool I used was [BootIt NG]("http://www.bootitng.com/").  For me, it worked fine and I can dualboot with no problems.

As far as completely ditching Windows or not... well that depends on your circumstance.  For me, as much as I want to switch completely, it just isn't practical right now. I have a printer (all in one) that isn't supported in linux, an MP3 player (Sony) that isn't supported in linux (though, maybe I can use wine, not sure), and a PDA (Clie TH55) that I can't get to synch with linux to save my life.  I am just not in a position to replace all of these items right now, so I am a little stuck.  Also, since I do some consulting work, I need to be able to plug in my laptop to a customer's network, select a networked printer, and print various documents.  With Windows it is quite painless.  I can't afford to show up at a client site only to realize that their printer doesn't have linux drivers available.  I can't very well tell them to wait while I google to see if I can find a way to get it to work.  So for me, I have a need to dual boot right now.  

I would say you should ask yourself if you have a "need" to dualboot or maybe just uneasy about being disconnected from the MS tether.  Either way why not just dual boot for a while.  That way you do have the option of booting back into Windows if you feel you must.  You may find that in a few months you haven't booted back into Windows at all.  That would be a good sign that for you a complete switch to linux wouldn't be a problem.

I hope this helps a bit.

---

### Post by seshomaru samma on 2006-08-17
I would personaly run a dual boot
You can create 3 partitions
The first is your Windows (NTFS)
The second can be a files and documents to be shared by both systems (FAT)
The third will be Ubuntu (EXT3)
It's best to keep Windows for a while. Ubuntu is friendly , but that doesn't mean that in a few weeks you will reach the same level of proficiency you have in Windows (well, depending on your proficiency...). It takes a while to get use to . 
For example , I sometimes like to write Chinese documents from top to bottom which Open Office in Linux does not support. In that case keeping my Windows partition is useful. Or let's say you have some problem , you can't connect to the internet or play CD or something like that , then you boot into Windows and check if the problem persists , this will give you a good perspective.

---

### Post by 3rdalbum on 2006-08-18
I always tell people to do a dual-boot. If for nothing else, you'll need your existing Windows installation as a source of native DLLs for Wine.

In Windows, you must defragment your hard drive before installing Ubuntu. Then when you get into the Ubuntu installer, you can tell it to non-destructively resize your Windows partition.

I'm using roughly 12 gigs in Ubuntu, but then I have quite a bit of stuff installed. I wouldn't recommend having less than 5 gigs for Ubuntu; you'll need room to move!

I haven't used the Live CD installer so I can't really give any step-by-step instructions. As long as you read the documentation on the CD and pay attention to what the installer is telling you, you should be fine. And remember to defragment on Windows before running the installer!

---

