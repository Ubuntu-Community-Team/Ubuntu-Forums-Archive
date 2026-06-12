---
title: "250GB disk partitioning problem."
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Pablo90 on 2007-06-26
Hi all!
I have the problem with partitioning my harddisk (250 GB). As you know Ubuntu can't make partitions above 200GB, so I can't devide it standart ("/"-10GB, "swap"-512MB and "/home"-rest), because the "/home" partition will be too big. I want do make use of all disk. Can anyone more advenced than me write here, how I should partition my disk?

---

### Post by REDISISTone.nl on 2007-06-26
> **Pablo90 said:**
> Hi all!
I have the problem with partitioning my harddisk (250 GB). As you know Ubuntu can't make partitions above 200GB, so I can't devide it standart ("/"-10GB, "swap"-512MB and "/home"-rest), because the "/home" partition will be too big. I want do make use of all disk. Can anyone more advenced than me write here, how I should partition my disk?

If you are dual booting you might want some space to exchange files between windows and linux (fat32)

Or just make it ext3...and it will be there for storing files !! :D

How I would do it?

1 GiB "swap"
10 GiB "/"
20 GiB "/home"
219 GiB "your ext3 file storing partition" (or split this one if you dual boot in fat32 (and have windows on some other HDD)for file storage)

---

### Post by alienexplorers on 2007-06-26
You could add a video or mpg3 partions if you use them.  You can basically add partitions for almost anything.  I have one for just family history stuff.

---

### Post by derby007 on 2007-06-26
Are u sure that the limit is 200GB, i think it 2TB for ext3.

---

### Post by REDISISTone.nl on 2007-06-26
[http://en.wikipedia.org/wiki/Ext3#Size_limits]("http://en.wikipedia.org/wiki/Ext3#Size_limits")

---

### Post by Pablo90 on 2007-06-26
Yes, I'm sure, because when I wand to make partition (ext3 file system) I see  announcement: "Can't have the end before the start". Have anyone the same problem?

---

### Post by anaconda on 2007-06-26
if you have 250GB hd you should really give "/" a bit more than 10GB.. It is really annoying if you get the "/" full, and would have plenty of free space in your hd. Just remenber that almost all programs you install go to "/"  so even one DVD, that (stupidly )wants to install itself to /usr/bin or somewhere will eat half of your "/"

or if you want to eg. rip DVDs, some programs want to copy the temporarily files to /tmp.. so you might need some more space in your "/"
If I was you I would make the "/" atleast 20GB maybe even more. And the space isn't wasted. you can use the "extra" space for storage if you dont need that much.. 

The recommendations to make "/" 6GB or 10GB are meant for SMALL hd:s and they are more like the minimum.. not the optimum sizes..

And it should be possinle to make ext3 partition bigger than 200GB

What program are you using when you are trying to make the partition? Some partitioning programs can have their own limitations.

---

### Post by bigken on 2007-06-26
strange two of my work stations have 250gig hdd and I have never had any problems formating them

10 gig / root
2gig swap 
the rest /home

update sorry I split whats left into two partitions

---

### Post by Pablo90 on 2007-06-26
OK. Thx all for help me. I find on this forum, that the problem is Ubuntu Live CD, because program, which it use to partitioning can't make partition above 200GB. But it will be possible to make the bigger partiton if I use alternate CD. 
@anaconda I have thought that programs are installing on /home partition (I'm total newbie). If they are installing on "/", then for what is use "/home" partition? Is it the same as "My documents" in Windows?

---

### Post by Jimmyfj on 2007-06-26
Just been searching the net for that answer - Seems that maximum disk size on ext3 with 4 Kb block size is 8 TB - With 8 Kb block size it's stunning 32 TB for filesystem (on alpha):

[http://www.lupaworld.com/35714/viewspace_17113.html](http://www.lupaworld.com/35714/viewspace_17113.html)

---

### Post by anaconda on 2007-06-26
> **Pablo90 said:**
> @anaconda I have thought that programs are installing on /home partition (I'm total newbie). If they are installing on "/", then for what is use "/home" partition? Is it the same as "My documents" in Windows?

Well. yes. In home I usually have mp3:s, movies, and lots of personal data, and then there are all your personal settings. etc..

but normal programs go to /usr/bin or /bin or somewhere else in "/". The programs you compile yourself you can put almost anywhere.

One other thing that takes more than 10GB from "/" is VMWares virtualmachines. I think the default directory for them is somewhere in "/", but ofcourse those can be kept in /home also. (I have about 20GB of virtualmachines.)

---

