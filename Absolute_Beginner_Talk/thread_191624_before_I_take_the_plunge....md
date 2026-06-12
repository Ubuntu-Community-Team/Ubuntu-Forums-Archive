---
title: "before I take the plunge..."
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by sameerkale on 2006-06-07
Hello everyone, first post. After my XP crashed for the eighth time in the last two months (this time from a *windows security update*) I thought I might give linux a try. I reas everything Wikipedia had to offer on the subject. Then I found this place. 

I downloaded the ISO and burned it, and over the last few days got sorta comfortable with it. But, as I have never done something like this before, I'm a bit nervous. I also have a few questions. I searched here and on google and I either could not find answers or did not understand them. My computer experience is like a mechanic on the moon, I can fix it reasonably well, but I have only a very basic idea how the darn thing works.

First, If this goes bad, can I always have both this and windows installed (and be able to switch back when I feel the need)? And, If I decide, uninstall one or the other later?

Second, I have a lot of documents/music on the computer I don't want to lose. At the same time, I have a lot of stuff(mostly programs) I would *love*to lose. On separate occasions I have ried to get rid of all the old programs and such, but I never had enough time. So, when you install this, will I also reformat the disk? And, if yes, can I selectively keep some files somehow? I really have no practical way at the moment of backing up 10GB of stuff. I have tried "partitoning"on my Dad's computer for something else last ear and I'd rather not do that. Also, Is it possible to use the music and documents on both systems without making a second copy of everything?

Third, How much space do I need? I have a 40(actually 37.2)GB hard drive with about nine free. I am currently close to broke, and can't really buy more space. Also, other than the ten GB I need, I only vaguely know where all of the space is taken up. Mostly programs, I think, but I'm not certain.

Thanks ahead for anything.:)

---

### Post by uzi09 on 2006-06-07
[QUOTE=sameerkale]Hello everyone, first post. After my XP crashed for the eighth time in the last two months (this time from a *windows security update*) I thought I might give linux a try. I reas everything Wikipedia had to offer on the subject. Then I found this place. [/quote]
welcome!
[QUOTE=sameerkale]
First, If this goes bad, can I always have both this and windows installed (and be able to switch back when I feel the need)? And, If I decide, uninstall one or the other later?
[/quote]
i'd recommend dual booting so that you can always switch back to windows to run those programs (like games) that don't run in linux.
also, if you have problems too. if you're really worried, i'd recommend playing with the live cd for a while since when u format/re-partition your drive, you have a chance of really screwing things up -- but for the most part it's very safe.
i'd recommend this guide:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[QUOTE=sameerkale]
Second, I have a lot of documents/music on the computer I don't want to lose. At the same time, I have a lot of stuff(mostly programs) I would *love*to lose. On separate occasions I have ried to get rid of all the old programs and such, but I never had enough time. So, when you install this, will I also reformat the disk? And, if yes, can I selectively keep some files somehow? I really have no practical way at the moment of backing up 10GB of stuff. I have tried "partitoning"on my Dad's computer for something else last ear and I'd rather not do that. Also, Is it possible to use the music and documents on both systems without making a second copy of everything?
[/quote]
well, you'll have to manually delete the stuff you don't want, but the rest can stay and you can just defragment your drive and partition it without loosing any data. a program called qparted (similar to partition magic) allows you to do this - and it's absolutly free! google it and you'll find a good cd for it.
as far as using things on both os's -- linux can READ from an NTFS partition BUT NOT WRITE! if you have a fat32 partition, then it'll be able to read/write, but not recommended since it has bad permissions settings. i'd recommend creating a seperate partition for the files you'd like to keep (/home) and install a program that lets you read files in windows from linux ([http://www.fs-driver.org)](http://www.fs-driver.org)).

[QUOTE=sameerkale]
Third, How much space do I need? I have a 40(actually 37.2)GB hard drive with about nine free. I am currently close to broke, and can't really buy more space. Also, other than the ten GB I need, I only vaguely know where all of the space is taken up. Mostly programs, I think, but I'm not certain.
[/quote]
you could really do it under 10gigs no problem. i'm sure some space will free up when you get rid of those things you don't want anymore. you can always go back and resize your partitions using qparted

[QUOTE=sameerkale]
Thanks ahead for anything.:)[/QUOTE]
you're welcome :D

---

### Post by sameerkale on 2006-06-07
Ive started to read the "Illustrated Dual Boot Site". It sounds good.

More questions, I didn't want to start a new thread:

I'm lookin at this program WNE or something, that adds a "compatability layer" so you can run some windows programs on Linux. Any experience with that?

---

### Post by aysiu on 2006-06-07
If you're using the Desktop CD instead of the Alternate Install CD, you may want to look at this:

[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

Keep in mind--it's always better to take it slow. Back up your data. Use the live CD for a while. Then dual boot. Then get rid of Windows. One step at a time.

Ask a lot of questions.

---

### Post by robins_web on 2006-06-07
I'd recommend an ancienr practice that hardly anyone uses anymore before you start: *back up your files!* I know you're careful and never make any mistakes; I'm that way myself. But it didn't keep me from losing several critical files. Fortunately, I had backups.

Remember Robin's First Rule of Computing: ***_[COLOR="Red"]Be Paranoid and Compulsive![/COLOR]_***

---

### Post by goobers on 2006-06-07
I installed ubuntu in a seperate partition and dual boot it with windows. I just mess around in linux and if i mess it up, i just reinstall. The installer has the option of removing all linux partitions to start fresh (i think it does anyways... i might be thinking of the Fedora Core 5 installer). The installer automatically configures bootloaders, so you don't even have to mess around with that.

I'd definitely reccomend backing up tho. And when you do get some spare cash, i reccomend an external hard drive- so useful for backing stuff up ;-)

---

