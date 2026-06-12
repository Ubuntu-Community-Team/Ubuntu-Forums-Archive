---
title: "looking for good DVD ripper and editor"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by Kulgan on 2006-11-25
I have been looking around in synaptic for a good dvd ripper, and ended up with AcidRip. I tried ripping a DVD and got it in french. Not quite what I want, really. The language was set to english, but it did it again the second time. 

Is there somebody who can explain how to fix it, or suggest a ripper that does things in english? 

Also, I was looking for a video editor that allows you remove a selection of a video. Just that simple, but preferably something that can edit avi vids. 

Any suggestions appreciated,
-K

---

### Post by Kulgan on 2006-11-25
Found the editor - avidemux works great for me :D

---

### Post by jerrykenny on 2006-11-25
kulgan,    dvdrip is very good, foolow the instructions on the ubuntu wiki

---

### Post by Kulgan on 2006-11-25
The "dvdrip" in the repos is nothing like the "dvd::rip" that you get when you google it - [http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/). It's giving me a pain in the rear... I'll keep at it, though ](*,)

---

### Post by Xtyn on 2006-11-25
:)

---

### Post by Kulgan on 2006-11-25
trying everything - I'm reformatting soon, so I'm not being cheap on space :P

3kb is getting what I have tried until now in english, so that's great, and I'm encoding it now, just to see how that works out...

---

### Post by Kulgan on 2006-11-25
well, so far the only way I have been able to use k3b for making avi files is title by title - and that's not really what I want... When copying the entire DVD, I get a regular image, as far as I know.

any ideas?

-K

---

### Post by coalastonmatt on 2006-11-25
It seems most required packages for this aren't available for edgy. Any other suggestions?

---

### Post by tagra123 on 2006-11-25
grip works great fo ogg and mp3


I think it's in the universe repos.

K9Copy is good but if it won't decrypt then --

Using wine the follow two programs work great to make backup copies.

DVD Decrypter
DVD Shrink


Here's the how to:

[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)

---

### Post by jerrykenny on 2006-11-25
I'm on Debian testing now, so not sure about the latest dvdrip on Ubuntu, certainly it was excellent on Hoary and Breezey,  I wonder if theres a lack of certain dependancies ?  

From the command line, dvdbackup is fast and reliable . . . .

If you find dvdrip craps out halfway thru, you can still continue processing using the command line with "transcode"

You'll need an xvid4.conf file in the working directory

---

### Post by Marsolin on 2006-11-26
> **Kulgan said:**
> well, so far the only way I have been able to use k3b for making avi files is title by title - and that's not really what I want... When copying the entire DVD, I get a regular image, as far as I know.

any ideas?

-K

What is your goal? Back in June I wrote an [article]("http://linuxappfinder.com/dvd_rippers1.php") describing my impressions of a number of different DVD rippers.

---

### Post by Kulgan on 2006-11-26
my goal is to stick a dvd in my drive, and make a single .avi file out of it that I can edit to my heart's desire. 

> 
From the command line, dvdbackup is fast and reliable . . . .

that seems to just be recreating the file structure that already was on the dvd - or does it change that at the end?

---

### Post by Kulgan on 2006-11-26
dvdbackup is also giving the vob files in that "avi on Totem" feel, with the contrast. I am getting a little pissed now... 

Is there a good program for windows that might do the trick? Much as I don't want to go into windows, if it will work, I am willing to brave the blueness...

---

### Post by RichJacot on 2006-11-26
I haven't make .avi files from dvd's but you might want to try k9copy to create an .iso, then maybe you can make the .avi from that.  Just a thought.

---

### Post by Kulgan on 2006-11-26
an iso would mean that it copied everything on the CD, including ALL the languages. I'm not sure there would be any difference between making an ISO and using the DVD itself...

---

### Post by RichJacot on 2006-11-26
With k9copy you can select what language(s) you want, chapters, special features, etc....

---

### Post by Kulgan on 2006-11-26
really? I thought you meant it made an ISO of the entire disk, rather than just the stuff you wanted - I'll give it a try!

---

### Post by Marsolin on 2006-11-26
[K3b]("http://linuxappfinder.com/package/k3b") and [dvd::rip]("http://linuxappfinder.com/package/dvdrip") will both convert a DVD to an AVI. I use K3b for that myself and it works well.

---

