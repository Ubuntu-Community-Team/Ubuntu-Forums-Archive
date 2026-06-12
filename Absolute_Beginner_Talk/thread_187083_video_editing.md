---
title: "video editing?"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by unicycler on 2006-06-02
Any programs to edit video?

---

### Post by IYY on 2006-06-02
Kino

---

### Post by %hMa@?b&lt;C on 2006-06-02
cinelerra, avidemux, jahshaka, diva. the list goes on and on.  Cinelerra is my favorite
[http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)

---

### Post by lapsey on 2006-06-02
Doesn't cinelerra require really high specs?

---

### Post by kelster on 2006-06-02
Hey I found the lives .deb somewhere, it is pretty cool, but if you want to edit a movie or tv ep it seems like it loads in real-time (ie.slow).  

k

---

### Post by nalmeth on 2006-06-02
I really like avidemux, but have heard Cineralla is great

---

### Post by gunksta on 2006-06-02
Cinelerra doesn't require anything crazy terrific. It has worked well enough for me on a 2 GHz AMD and a 2.4 GHz P4. True, these aren't slow machines, but neither has more than 512 MB of RAM or super amazing graphics cards. I would say it needs a solid, modern machine, but not a super machine.

---

### Post by gratefulfrog on 2006-06-05
I've been running cinelerra and kino for nearly 2 years.

Each tool has strong points. I haven't upgraded cinelerra in 12 months and am about to do so, I hope it's become more stable.

I process DV into TV viewable DVD's as follows:

[LIST=1]
[*]capture with dvgrab at the command line (dvgrab is the command line "version" of kino), 
[*]then edit and render with cinelerra, 
[*]then use ffmpeg to convert to mpeg-2
[*]then use dvdstyler to build the DVD's menus and write the DVD files
[*]finally burn the DVD iso image directly with nautilus.
[/LIST]

Setting this up and using cinelerra aren't straightforward (check my page [http://gratefulfrog.net]("http://gratefulfrog.net") for some help which dates from last year). Also the cinelerra IRC is full of great and always helpful people willing to talk you through anything!

If you want to make short, simple edits, and render for Internet, then you probably won't need much of a machine. Rendering is where the cost comes. This will always require power and memory, best to use a farm of machines if you're making full length feature film ;-)

If you want to do serious video editing (lots of footage, lost of effects),  you need memory, 2 Gb is comfortable for cinelerra. 

Let me know how you get on!
Ciao,
GF.

---

### Post by MattCarp on 2006-06-05
I've tried Kino and LiVES.

Kino (0.8.0) - seems like the way to go.  Having said that, I still think it's not quite as intuitive as Windows Movie Maker (gasp!).  In particular, effects and titles.   Plus I prefer WMM's method of displaying the video timeline.  I did just find this tutorial:  [http://yourmachines.org/tutorials/kino.html](http://yourmachines.org/tutorials/kino.html)  So, I hope to better learn how to use it.

I did have an issue exporting video to mpeg-2, but I just needed to install the mjpegtools package.

LiVES.  LiVES requires mplayer.  I've been unable to edit a video with LiVES - first, whatever LiVES does when you open a video file, it's incredibly slow.  Next, whenever try playing video in the tool the audio and video is out of sync.  Finally, I don't see how I can do the simple video editing that I need.  It may do it, but at this point I can just say it does not have an intuitive UI.

Cinelerra sounds fun, but frankly, I don't have time to learn how to make it work.  Besides, I have just a 1.4GHz PIII, so I'm worried on that front.  I'd love to be able to use an exciting powerful tool like it, but it's gotta be easy to install, easy to use, and be stable.

I haven't heard of avidemux, diva, or jahshaka.

---

