---
title: "want to get a new hd for linux"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by SurlyDune on 2008-04-06
I had a problem with a hard power down and ive spent about 8 hours trying to get it fixed. i've run into problems mounting my partition  or doing any sort of recovery. I think the problems are because my hard drive is was formatted in ntfs and apparently linux doesn't run on that to well. So i guess my question is are there some hd brands more compatible with linux (i've glanced over something that said seagates had problems) and then what type of formating i should use and should the second hd be set up as a slave or any other useful info. thanks

---

### Post by perezmaximus on 2008-04-06
On may desktop I am running both XP and UBUNTU 7.10 but I'm using 2 hdd one for XP the other for UBUNTU.The hdd I have ubuntu installed is a seagate,since I didn't partition the hdd I let the live cd do it automatic.I have no problems running the seagate hdd .

---

### Post by Hospadar on 2008-04-06
Well there must be a non-ntfs portion of your hard drive for linux to be installed on, since you can't install it on an ntfs partition.  Do you only have one drive? Could you list the output of "df" (run in a terminal).

Also, your problems sound like a bad drive, but before droppin the bucks on a new drive, you might want to 
1) post specific mounting errors
2) let us know exactly what you are doing when you run into problems
3) run a hard drive test with something like the [ultimate boot cd]("http://www.ultimatebootcd.com/").  This is what I use at work to test hard drive.  You boot up with the cd, then go to hard drive tools, and run a quick drive test, you can pick any of the different brands of hard drive test, they'll all work.  It takes a couple hours and can really provide some valuable insight as to the source of your problems.

As for buying a new drive, I think any brand should be fine.  I usually buy western digitals because of the price.   I'd browse around on newegg.com and read the user reviews, most drives are pretty much the same thing, so you won't have to try to hard to find a good drive (also newegg is a great place for buying hardware, it's very cheap)

---

### Post by SOULRiDER on 2008-04-06
I dont know of any brands that have issues, but you never know....

If you get a new drive make sure you format it as Ext2 or Ext3, you wont be able to write/read from windows but it will be fully supported by Linux.

---

### Post by yamfox on 2008-04-06
I have a WD (Weatern Digital) hd it it works like a charm. At 320 gb, you can't go wrong at the price I bought it at... $80

---

### Post by SurlyDune on 2008-04-06
here's the forum where i list my problems [http://ubuntuforums.org/showthread.php?t=746880](http://ubuntuforums.org/showthread.php?t=746880)

---

