---
title: "Recommend app to extract mpg from dvd"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by r76 on 2007-06-03
I want to extract some files that i recorded as video dvds - how can i quickly get mpeg-2 video files off the discs?  I don't want to transcode or anything like that.  I recorded each dvd with several titles and a menu, nothing too complicated, but I'd like to be able to select a title on the dvd and save it to the hard drive as mpeg-2 video.
Thanks :)

---

### Post by cantormath on 2007-06-03
> **r76 said:**
> I want to extract some files that i recorded as video dvds - how can i quickly get mpeg-2 video files off the discs?  I don't want to transcode or anything like that.  I recorded each dvd with several titles and a menu, nothing too complicated, but I'd like to be able to select a title on the dvd and save it to the hard drive as mpeg-2 video.
Thanks :)

have you tried dvdrip or handbrake?

---

### Post by vanadium on 2007-06-03
Avidemux can open DVD VOB's and save the output in DVD compliant mpg's (or separate video and audio streams) without transcoding.

---

### Post by r76 on 2007-06-03
Cheers, those suggestions are much appreciated.  I tried dvd::rip but I couldn't find a straightforward copy option.  Acidrip slowed right down while I was using it, I also tried k3b and k9copy.  [Vobcopy]("http://lpn.rnbhq.org/projects/c/c.shtml") came close but seemed to want to do the whole dvd, not individual titles, then i found [here]("http://ubuntuforums.org/showthread.php?t=56617") this simple command:
```
mplayer -dumpstream -dumpfile movie.mpg dvd://1
```
which copies title 1 to a single mpeg, and seems to be quick with no obvious loss in quality :D

I did find all those programs on [linux app finder]("http://linuxappfinder.com/multimedia"), which was a really useful site, for future reference.

---

