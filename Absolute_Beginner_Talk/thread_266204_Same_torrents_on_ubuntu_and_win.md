---
title: "Same torrents on ubuntu and win"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by DarthSudaka on 2006-09-26
Hello,
I have a question,
I sometimes boot in Ubuntu, sometimes have to in Win.

Is there a way I can download the same torrents on both? 
What I want to do is, eg, I boot in win, and start downloading a torrent in, say, bitlord or utorrent. 
Next time I boot Ubuntu and I want to resume downloading that .torrent in Azureus (or other client).

Is that possible?



(I guess first I should make my Ubuntu able to write on NTFS partitions, but there's enough documentation and I think I'll be able to do it.)

---

### Post by jISh on 2006-09-26
Sure. Azureus would take some time and do a hash check of the files, but once it's got it figured out the download will resume.

---

### Post by DarthSudaka on 2006-09-27
Cool! thanks!! :D 

now... getting more picky..... is that only possible with Azureus?
(I don't like it much.. takes up too many resources)

---

### Post by bodhi.zazen on 2006-09-27
This should be true of all torrent clients. It is in their nature.

You may want to check out utorrent. It is very easy in both windows and Linux:

[[color=blue]utorrent[/color]](http://ubuntuforums.org/showthread.php?t=191161)

---

### Post by orb9220 on 2006-09-27
Yes utorrent will run under wine for the linux side. And if you setup a  fat32 partition then xp and linux can read and write to it.

---

### Post by DarthSudaka on 2006-09-28
did it!!
I have to make "both" utorrents load all the .torrent files on startup.

works like a charm... thanks a lotttt!!! :D

---

