---
title: "Music on boot? Is this feasible?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2008-03-05
I'm just wondering, I want my PC to play a song while it boots. Like, after I select ubuntu on grub (Better yet, when I start grub) could my PC play a song? I'm thinking all I would need to start is for it to start MPD, everything MPD needs to work, and then the command mpd /path/to/song

---

### Post by PinkFloyd102489 on 2008-03-06
You can throw the MPD command into rc.local, which will execute during boot but not immediately after selecting.

---

### Post by jordank on 2008-03-06
I'm quite sure this is possible, but I think you have to ask yourself if you really want to do this.  I've done it on a windows box, but I definitely got over it in the same day.  As sweet as it sounds, i think you may just get really sick of it.

Just a word of caution :)

---

