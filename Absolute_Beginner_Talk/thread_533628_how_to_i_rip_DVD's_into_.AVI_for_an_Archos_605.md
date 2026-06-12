---
title: "how to i rip DVD's into .AVI for an Archos 605"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by tobyfountain on 2007-08-24
Hi, please can someone tell me how to rip DVD's into an .AVI file. I only want the movie, not the menus or anything.
What programs should I use?
and could you please give me an estimation of the time it should take?


thanks

---

### Post by Hallvor on 2007-08-24
It all depends on your needs. If you just want something very simple, I recommend Acidrip. It reads the DVD straight from the DVD-rom and encodes it to an .AVI. The only bad thing about it is that it doesn`t seem to hit correct file size. If I want a 700 MB .AVI, it is probably something like 670 MB. I also had problems getting rid of black borders. It was supposed to have an autodetect feature, but I never could make it work properly. 

If you want to make high quality  DVD-rips, I recommend DVD::Rip. It has tons of options, copies the DVD to the hard drive before encoding and doesn`t strain the DVD so much. Hits the correct filesize. Better quality rips.

About time: Encoding a movie to .AVI is a real CPU killer. How long time it takes depends on your CPU, but on my computer from 2003, it usually takes a few hours to make a two pass XviD (about 20 frames per second). Two passes will give you better quality, but it also takes twice as long to encode.

---

### Post by anaconda on 2007-08-24
I use k9copy, because it is easy to use.

---

### Post by Amazona aestiva on 2007-08-24
Maybe Acidrip does it.

---

### Post by tobyfountain on 2007-08-24
would it be quicker if it was in mpeg format?

for reference, my cpu is dual core 1.8ghz

---

### Post by Hallvor on 2007-08-24
> **anaconda said:**
> I use k9copy, because it is easy to use.

AVIs with K9copy?:confused:

---

### Post by Hallvor on 2007-08-24
> **tobyfountain said:**
> would it be quicker if it was in mpeg format?

for reference, my cpu is dual core 1.8ghz

Quick means bad quality. Good quality rips will take its time; there are no shortcuts. Just encode the movie at night, and you`ll have a great quality n-th pass XviD in the morning. :)

---

### Post by Pocadotty on 2007-08-24
DVD::rip works well, however when i encode selected chapters it puts each chapter in its own file.  Is there a way to merge them with dvd::rip, or change a setting so it rips the session to 1 file.

If not, what is the best way to merge them to 1 file while maintaining format?

---

### Post by brennydoogles on 2007-08-24
DVD::rip looks good for me, but is there a way to have it rip from a .iso?? I make backups of all of my dvd's as .iso, but sometimes an avi would be wonderful. any ideas??

---

### Post by Pocadotty on 2007-08-24
you could probably mount the iso with Gmount (or something like it) and then rip as normal...

---

### Post by brennydoogles on 2007-08-25
> **Pocadotty said:**
> you could probably mount the iso with Gmount (or something like it) and then rip as normal...

is gmount always in french, or did aptitude install it incorrectly??

---

### Post by Pocadotty on 2007-08-26
It is now... for some reason... I remember it not being that way... but it is a pretty easy interface so you should be ok... or if you want you can mount by terminal command... But I always prefer GUI's...

---

### Post by anaconda on 2007-08-28
> **Hallvor said:**
> AVIs with K9copy?:confused:

Yes. K9copy can make divx or xvid from a DVD. 
Don't remember if it actually can put the .avi ending, but as .avi is just a container and inside it usually is xvid or divx.. what is the difference?

---

### Post by Hallvor on 2007-08-28
> **anaconda said:**
> Yes. K9copy can make divx or xvid from a DVD. 
Don't remember if it actually can put the .avi ending, but as .avi is just a container and inside it usually is xvid or divx.. what is the difference?

Didn`t know that. I`ll look into it. I only use K9copy for full DVDs, and DVD::Rip for XviDs...

Edit: Found this [http://duggmirror.com/linux_unix/Ripping_DVDs_to_MPEG4_with_K9Copy/](http://duggmirror.com/linux_unix/Ripping_DVDs_to_MPEG4_with_K9Copy/)

---

### Post by Amstell on 2008-01-10
I use DVD:rip for encoding my dvd's.  Works great and great resolution with my 605

---

### Post by timbounceback on 2008-01-10
give acidrip (uses mencoder) a try, or, if you would prefer to use the command line, just plain mencoder.

---

### Post by michaelzap on 2008-01-10
I get the best-quality xvids using Avidemux. Just select the first vob file on the DVD (or whichever one begins the main movie set) and answer yes when asked if the program should combine them. Then select whatever settings you want and save out the file.

For some reason, Acidrip doesn't give me nearly as good results as Avidemux. I recently made an xvid of a movie with it and even at 1.2GB the quality was rather poor (two passes, etc.). I was able to make the same move look a lot better using Avidemux, and the final filesize was only 700MB.

This may be specific to xvids, but Avidemux has never let me down yet.

---

