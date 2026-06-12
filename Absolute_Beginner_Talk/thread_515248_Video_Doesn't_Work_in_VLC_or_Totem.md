---
title: "Video Doesn't Work in VLC or Totem"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by crsd36 on 2007-08-01
I'm wondering if I'm still missing a codec although I installed all codecs that I know of and was under the impression that VLC came with all codecs pre-installed...

My problem is that sometimes the video shows, but disappears; and other time the video doesn't appear at all.  Either way, the sound works.  I have tried using a DVD and a DVD rip and always have the same problem so I'm assuming that I'm still missing something.

Any help is greatly appreciated!

---

### Post by bren on 2007-08-01
you could try installing the codecs mentioned here to check?

bren

[https://help.ubuntu.com/7.04/musicvideophotos/C/index.html](https://help.ubuntu.com/7.04/musicvideophotos/C/index.html)

---

### Post by crsd36 on 2007-08-02
> **bren said:**
> you could try installing the codecs mentioned here to check?

bren

[https://help.ubuntu.com/7.04/musicvideophotos/C/index.html](https://help.ubuntu.com/7.04/musicvideophotos/C/index.html)

Hi, I tried going through that and something still isnt working properly.  Same problems as before...it is EXTREMELY sensitive ie. the video starts (most of the time) and as soon as I move my mouse it turns to a black screen.  The same problem for DVDs/AVIs/etc.  Again, any help is most appreciated!

---

### Post by Paulmd on 2007-08-02
> **crsd36 said:**
> I'm wondering if I'm still missing a codec although I installed all codecs that I know of and was under the impression that VLC came with all codecs pre-installed...

My problem is that sometimes the video shows, but disappears; and other time the video doesn't appear at all.  Either way, the sound works.  I have tried using a DVD and a DVD rip and always have the same problem so I'm assuming that I'm still missing something.

Any help is greatly appreciated!


1) Disable beryl or compiz, if it's running. (the desktop effects)

2) In VLC, if the video diasappears, right click on the blank spot where the video should be, and select deinterlace, and change the option. It doesn't matter what you change it TO, as long as it's changed. This is screwy, and is probably a bug in VLC.

---

### Post by crsd36 on 2007-08-02
> **Paulmd said:**
> 1) Disable beryl or compiz, if it's running. (the desktop effects)

2) In VLC, if the video diasappears, right click on the blank spot where the video should be, and select deinterlace, and change the option. It doesn't matter what you change it TO, as long as it's changed. This is screwy, and is probably a bug in VLC.

That solves it thank you!  Do you have recommendations for submitting this possible bug?  Thanks again!

---

### Post by atomkarinca on 2007-08-02
it shouldn't be a bug because i have used compiz, beryl and compiz fusion and i haven't had a problem like this before. but you can play with the video settings of the players.

---

### Post by Paulmd on 2007-08-02
> **crsd36 said:**
> That solves it thank you!  Do you have recommendations for submitting this possible bug?  Thanks again!

I have already done so to ubuntu, but you could certainly add details (my original bug report was a bit [make that a lot] lacking). And it would be nice to see a confirm.

[http://www.ubuntu.com/community/ReportProblem](http://www.ubuntu.com/community/ReportProblem)

[https://bugs.launchpad.net/ubuntu/+bug/129386](https://bugs.launchpad.net/ubuntu/+bug/129386)

I have not submitted a bug to Videolan, so a note to them would be nice.

[http://www.videolan.org/](http://www.videolan.org/)

Scroll down a bit to the "Report Bugs" header.

---

### Post by walkerk on 2007-08-02
> **crsd36 said:**
> That solves it thank you!  Do you have recommendations for submitting this possible bug?  Thanks again!

try using [SMPlayer]("http://www.getdeb.net/search.php?keywords=SMPlayer").. VLC doens't work great for me with Compiz Fusion but SMPlaye works ok..

---

### Post by crsd36 on 2007-08-02
SMPlayer works great!  Thanks for the tip, I have no problems so far, best option yet.  Thanks again!

---

### Post by ayoli on 2007-08-03
you may want to read [this thread]("http://ubuntuforums.org/showthread.php?t=507332"), this worked for me quite good.

---

### Post by Netsurfer on 2007-08-14
Look at here: [http://ubuntuforums.org/showthread.php?t=524236&highlight=video+blank+winth+desktop+effects](http://ubuntuforums.org/showthread.php?t=524236&highlight=video+blank+winth+desktop+effects)

Maybe can help you!

Bye.

---

### Post by the_analyzer on 2007-10-13
Hey, I have the same problem, CAN WE WATCH MOVIES WITH DESKTOP EFFECTS ACTIVATED?
thnx

---

### Post by ayoli on 2007-10-13
> **the_analyzer said:**
> Hey, I have the same problem, CAN WE WATCH MOVIES WITH DESKTOP EFFECTS ACTIVATED?
thnx

yes, you should read this thread : [http://ubuntuforums.org/showthread.php?t=507332](http://ubuntuforums.org/showthread.php?t=507332) (already mentionned above)
solutions in it, just some configuration tweak for your favorite  players

---

