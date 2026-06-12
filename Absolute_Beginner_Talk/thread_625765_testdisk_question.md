---
title: "testdisk question"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by tomxyz on 2007-11-28
Hello all,

just used testdisk to recover files after screwing up my external hd (250gig maxtor), it found something and this is what I have now on my screen

1 E extended LBA  start 0 end 254
5 L hpfts-ntfs        start 0 end 254

I have two options, I can choose to write the partition structure to disk by pressing [write], or maximize/minimize the partition by pressing [extd part]

I'm guessing I have to press write but I'm afraid I will overwrite any data that could be still on there.

any advise?

regards Tom

---

### Post by mikewhatever on 2007-11-28
How come you do not know whether there is data on the disk? If you know there is valuable stuff on that disk, do not write to it.

---

### Post by tomxyz on 2007-11-29
thanks mikewhatever for replying,

How should I know in exactly what sectors the information is written? When I look in gparted the ntfs part streches out over the whole lenght. 
Anyway, testdisk said the bootsector was not ok, but the backup bootsector was ok and asked if I wanted to overwrite. Since it said the backup was ok I said yes.
Not much of an improvement, still can't acces my data.

Since the most important data are my childrens pictures (home computer not office one :) )
I unleashed photorec on it. I specified only Jpeg but it has been working for 13 hours now non stop and still has to go about 751 hours !!!??? (estimated) Is this normal??? (250gig external hd) (maybe because its connected to an USB1 port)

I'm starting to think I will have to find a way to explain the wife I lost all pictures of 2007 (I thought I had saved them somewhere else before starting this). Well, if she doesn't doesn't kill me, it will make me stronger!:) 

One of the reasons I changed to Kubuntu one year ago whas the support you get from people in this forum, but one thing I start to realize, it makes you to confidend!
You check threads for a couple of hours, and before you know it, you take the plunge and start "copy/pasting" commands in your terminal without always nowing exactly what they are doing. Ok, In my case I also bought the book ubuntu unleashed wich helps a lot but still...

thanks Tom

---

### Post by mikewhatever on 2007-11-29
750 hours is a long time. I doubt it should be taking that long, but can't really tell. What exactly is wrong with the drive? Can you mount it? Any error messages?

---

### Post by tomxyz on 2007-11-29
Well, when trying to repartition some of the ntfs to fat 32 it stopped in the middle with a blank error pupup? Couldn't do anything after that. In gparted I had two black rectangles, one where the ntfs was and one where the fat32 should have come.

When I connected the drive to another computer running xp it said disk not formatted, do you want to format it now, I said no.

I used testdisk replaced the bootsector with the backup, under ubuntu it said something like  wrong fs type, can't read superblock....
Under windows it just says drive is corrupt (another reason I switched to ubuntu).

Now I'm trying photorec, the past 3 hours it dropped from 750hrs to 270hrs (it's an estimated time) but 270hrs is still a very long time.

I'll see how it devellops.

thx Tom

---

### Post by tomxyz on 2007-12-05
just to warn anybody who's trying to use photorec on an external disk.
 
I bought my external disk of 250gig because the one in my laptop became to small 40gig.

When I started photorec I didn't exactly know how many gig's of pictures where on the external disk. I assumed around 20gig so I figured I had enough space on my laptop (since I have the external hd almost all my data gets stashed there) to store the recovered files.

Since (as you can read in my previous repley) it takes a very long time to recover, I left the computer running overnight. In the morning photorec was still running but I had to switch it off to go to work, (hoping to find a way to start again where I stopped it in the evening)

When I got back I couldn't start my laptop up again!! Apparently I had to much pictures on the external disk and photorec filled my computers hd untill there was no more room left. 
This made it impossible for the graphic interface to be loaded and I was left with the shell.

Weird thing is that altough the disk was already full when I switched it off in the morning, photorec was still scanning the rest of the disk, (although the amount of recovered files didn't go up anymore) It didn't give any indication that the target was full.

Now beside the external disk I was trying to fix, also my computer needs fixing.](*,)]

Luckly I now a grand ubuntu wizard who can do it, but it's going to cost me a couple of bottles :-P

regards Tom

---

