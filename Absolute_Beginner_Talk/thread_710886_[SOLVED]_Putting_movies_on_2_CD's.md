---
title: "[SOLVED] Putting movies on 2 CD's"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Carnivorum on 2008-02-28
Bs'd

How can I cut a movie in two, so that I can put a long movie on two CD's?

When I have a movie which is more than 700 Mb, and I put in a CD of 870 Mb, my burner doesn't want to burn it.  He tells me to put in a CD of more than 700 Mb, while there is already a big CD in it.

---

### Post by michael37 on 2008-02-29
> **Carnivorum said:**
> Bs'd

How can I cut a movie in two, so that I can put a long movie on two CD's?

When I have a movie which is more than 700 Mb, and I put in a CD of 870 Mb, my burner doesn't want to burn it.  He tells me to put in a CD of more than 700 Mb, while there is already a big CD in it.

Install Avidemux.  Using Avidemux, you can either split your AVI into two, or you can recode your movie with another codec so the total size is 700MB.  There are plenty of webpages on Avidemux usage, so I won't duplicate em here.

---

### Post by kpkeerthi on 2008-02-29
You need an editor line [avidemux]("http://fixounet.free.fr/avidemux/") to cut the video file into two and burn them individually.
```
sudo aptitude --with-recommends install avidemux
```

---

### Post by northern lights on 2008-02-29
Install "mencoder": ```
sudoapt-get install mencoder
```

in a terminal, enter:```
mencoder OriginalMovie.avi -o CD1.avi -ovc copy -oac copy -endpos 700MB
```for the first CD to be created. At the end of the terminal output, which will look something like: ```
Video stream: 1200.000 kbit/s  (1500000 B/s)  size: 638610165 bytes  3600 secs  10000 frames
``` note the number of seconds (codec/resolution/compression dependent) that made up the first CD, round that down to a full second. Suppose it was an hour (3600 seconds), then the second CD would be created like this: ```
mencoder OriginalMovie.avi -o CD2.avi -ovc copy -oac copy -ss 3600
```

Explanation of the syntax:

-ovc [option]: output video codec, in this case "copy" uses the one of your original file
-oac [option]: same thing, audio codec...
-endpos [option]: defines a cutoff
-ss [option]: defines a starting position in seconds
OriginalMovie.avi: to be replaced by name of original file
-o nameoffile.ext: defines name of output file

[EDIT]
late..
I suppose "avidemux" is a also a good option. Haven't checked it out. Will now.
[/EDIT]

---

### Post by Carnivorum on 2008-02-29
Bs'd

Avidemux works great.  

Thanks everybody for their input.

---

