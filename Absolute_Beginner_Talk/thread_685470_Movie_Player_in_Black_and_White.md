---
title: "Movie Player in Black and White"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by DasMatts on 2008-02-02
Hey All, 

My movie player has resorted to playing everything in black and white. Has anyone else had this problem?

Matt

---

### Post by smartboyathome on 2008-02-02
Which player are you using, the one that comes default in Ubuntu?

---

### Post by Fizzzy on 2008-02-02
I'm assuming your using the default one, in which most likely the problem is is that you don't have the right codec to play the movie file.

---

### Post by thelatinist on 2008-02-02
I'm not exactly clear what your problem is: were you formerly able to play videos in color? And, if so, do all videos (including videos you formerly could watch in color) now appear in black-and-white?  Or is it just that one particular video that you haven't played before doesn't play in color?

Also, what media player are you using?  Totem?  Mplayer?  VLC?

---

### Post by tizza10 on 2008-02-07
I too have this problem, it only happened a few days ago after an update. I managed to tweak the settings somehow to get colour back, but the colours are mixed/wrong. I removed totem-gstreamer because I noticed that if I ran it at all during a session it would make VLC worse. I had perfect video quality before this.
 Using fully updated 7.10, intel i810 graphics on an external LCD.
Mplayer picture quality is okay but it will not go full screen.
Any ideas?

---

### Post by prayag on 2008-03-09
> **DasMatts said:**
> Hey All, 

My movie player has resorted to playing everything in black and white. Has anyone else had this problem?

Matt

Try this:

rm -r ~/.gconf/apps/totem
login and logout. Should work !! Found[ here]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/149791")

---

### Post by Auslegung on 2008-03-09
I did this: <http://ubuntuforums.org/showpost.php?p=2896078&postcount=2> and it worked like a charm.  Essentially, go to Terminal and type ```
gstreamer-properties
``` and press enter.  Click on the Video tab, and under Default Output->Plugin change it to X Window System (No Xv).  Hit the Test button and a window should pop up with the usual TV test, the colored bars, you know.

---

