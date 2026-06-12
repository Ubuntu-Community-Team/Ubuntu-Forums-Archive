---
title: "Issues with dual booting"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by drewcoon on 2007-08-25
Hi, I've been looking into Linux for a long time (particularily, Ubuntu studio), I've been reading some tuts online for making a dual boot Win XP / Ubuntu PC, and the first step in all of them seems to be defragging your disk you are planning on partitioning to make sure nothing gets destroyed.

If you look at the pic of the defragmented computer on this tut:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)
you'll see that all of the data is neatly compacted into one section of the disk.

Now, here's my 180Gb main hard drive, as defragmented as I can get it:
[http://i16.photobucket.com/albums/b23/Drewc2k5/defrag.jpg](http://i16.photobucket.com/albums/b23/Drewc2k5/defrag.jpg)
notice how although there are almost no fragmented files, the data is still spread out across the disk.

Will this become as issue when I make the partition? If it's a problem, how would I go about fiixing it?

Thanks for help in advance, by the way :)

---

### Post by davidjmayo on 2007-08-25
how many times did you defrag your disk?
does doing it again&again many times make a difference?

---

### Post by drewcoon on 2007-08-25
I tried defragging it multiple times, but it just seems to stop a few seconds after it starts and it gives me a "defragmenting complete" message.

I'll click it a few more times and see if it does anything :p

---

### Post by xzero1 on 2007-08-25
The main reason you want to defrag before installing is to make contiguous space for your new partition -- much preferably at the end of your drive.This free space will be used as your new partition(s) for ubuntu. If you have your desired amount of megabytes free the you could install ubuntu, but it would be harder to defrag windows later since it will have less free space. I would suggest downloading perfect disk or another defragger to consolidate your free space before installing.

---

### Post by pgar23 on 2007-08-25
> **drewcoon said:**
> I tried defragging it multiple times, but it just seems to stop a few seconds after it starts and it gives me a "defragmenting complete" message.

I'll click it a few more times and see if it does anything :p

If you have defragged it multiple times and nothing has changed, just give up, nothing WILL change, seek alternate help on the defragging part....
(I dont think it will really matter, but I'm also no expert)

For the DUAL BOOT part....view my signature...it has a great VIDEO TUTORIAL on how to dual boot, its from google video.

|
|
|
V

---

### Post by drewcoon on 2007-08-25
Alright, i've run the defragmenter utility about twenty times, and it did make a difference. I've gotten all the data in one area, except three little jerk lines that just refuse to move:
[http://i16.photobucket.com/albums/b23/Drewc2k5/defrag2.jpg](http://i16.photobucket.com/albums/b23/Drewc2k5/defrag2.jpg)

I might just take a look for a better defragger... Is perfect disk free?

I'll be sure to watch that vid before I start too :)

---

### Post by xzero1 on 2007-08-25
Free and fully functional for 30 days. Should give you plenty of time.

---

### Post by pgar23 on 2007-08-25
> **drewcoon said:**
> Alright, i've run the defragmenter utility about twenty times, and it did make a difference. I've gotten all the data in one area, except three little jerk lines that just refuse to move:
[http://i16.photobucket.com/albums/b23/Drewc2k5/defrag2.jpg](http://i16.photobucket.com/albums/b23/Drewc2k5/defrag2.jpg)

I might just take a look for a better defragger... Is perfect disk free?

I'll be sure to watch that vid before I start too :)

Wow, good job with the defragg, I wonder y it wouldnt just do that  the first couple of times...oh well, at least you got it.
Now to move on, MAKE BACKUPS!!!!!<------------IMPORTANT
make backups even if you dont think its necessary, just in case something goes wrong/unexpected.
Or if you dont care, skip the backups and just watch the video.

---

### Post by drewcoon on 2007-08-25
Perfect Disk works like a charm... I did the Offline System file defrag, and it moves those lines near the end of the disk closer to the front (Perfect disk colors them as pink.. Which means they are boot related).

I have about 50% of my disk full of nice, clear, empty space now. I backed up some of my really important stuff, but as you can guess by my ~150 gigs of free space, I'm not exactly heavy on files. Most of my stuff that I would be afraid of losing is stored online, anyways.

Well, I have to give my system one more defrag, since a few files moved to the back (apparently it happened when I burned my Ubuntu onto a DVD?), Then it's off to the land of command prompts and ASCII pictures... Wish me luck :p

---

### Post by drewcoon on 2007-08-25
Okay, I got the partition done, and i'm still able to post here so I guess something went right :)

---

