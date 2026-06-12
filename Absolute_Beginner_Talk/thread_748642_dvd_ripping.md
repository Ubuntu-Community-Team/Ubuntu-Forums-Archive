---
title: "dvd ripping"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-04-07
I am trying to rip a dvd, it is not protected and belongs to the company I am working for, I have tried acidrip and dvd::rip and they both only see the first title out of 6 I cannont get either of them to see all six titles so I tried k9copy it see all six but when it goes to rip it just dies, no errors just dies.  So I installed devede and thoggen neither of which seemed to work at all.  Any advice, help?

Thanks

---

### Post by HermanAB on 2008-04-07
k3b?

---

### Post by TechDragon on 2008-04-07
I see where it says it can do this but when I click on it, it just stares back at me blankly.  Where is the "go" button.

Thanks

---

### Post by TechDragon on 2008-04-07
actually, I don't think I am saying this right.  I need to convert the contents of this dvd to xvid or wmv or something.  My field reps keep losing the DVD and I want to put it on their laptops for use.

Thanks

---

### Post by pseudo-random on 2008-04-07
Use mplayer to locate your dvd chapter of choice: ```
mplayer dvd://1
mplayer dvd://2
etc
```
Then rip it to an AVI with
```
mencoder dvd://1 - o movie.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4
```

FYI acid::rip is just a GUI front-end for mencoder. Doing it from the command line will give you more control and better feedback.

---

### Post by lackofcreativity on 2008-04-07
Seriously?? Wow. I didn't know that. I've been trying to do this forever.... Just pointing out, though, you might need the codec for mp4 if it's not there. I got mine from w32codecs.

---

