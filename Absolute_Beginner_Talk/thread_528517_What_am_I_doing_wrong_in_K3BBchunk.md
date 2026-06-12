---
title: "What am I doing wrong in K3B/Bchunk?"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Ylang on 2007-08-18
Alright, so I downloaded a movie that was in .bin/.cue format. I used k3b to attempt to make a video dvd, but to no avail. Then I tried to convert to .iso using bchunk. Everytime I try to convert the files however, I get an error reading:**_ "No such file or directory"_**. I have checked my spellling and capitalizations, and I still cannot figure out what is wrong. Sorry, but I am pretty new to Ubuntu, so I am really bad at this.

---

### Post by Ylang on 2007-08-18
Never mind, I figured it out. Apparently, the whole file path is necessary for bchunk to run. Also, if you have spaces in your file name (as mine did) either rename it, or put it in quotes when you type it in terminal. Now I have the .iso file and I can use it for k3b.

---

### Post by Ylang on 2007-08-19
Well I supposedly got the .iso conversions working, but what I didn't know was that bchunk converts the .bin/.cue files into TWO .iso files, one of them is 695.5MB and the other is 600KB. I tried using K3B to burn a DVD image file, but whenever I put the big file, it says it isn't a Iso9660. And the smaller file is the correct format, but it doesn't work in a DVD player. Is there a way to put these TWO .iso files on a DVD so that it is usable in a regular DVD player?

---

