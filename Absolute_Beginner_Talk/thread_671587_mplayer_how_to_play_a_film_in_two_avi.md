---
title: "mplayer: how to play a film in two avi"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by netimen on 2008-01-18
I have a film wich is split into two files part1.avi and part2.avi. If I use
```
mplayer part1.avi part2,avi 
```
there is a very big delay between finishing of part1 and starting the part2. How can I eliminate this delay?

---

### Post by Zurd on 2008-01-18
If both files are identical in the video codec and audio codec they use (run the command file part1.avi part2.avi to make sure of  that) then run mencoder -oac copy -ovc copy -o new_movie.avi part1.avi part2.avi to merge both files into one, now there's no delay.

---

### Post by netimen on 2008-01-19
But it's not convenient - especially if I also have subtitles split in two files

---

