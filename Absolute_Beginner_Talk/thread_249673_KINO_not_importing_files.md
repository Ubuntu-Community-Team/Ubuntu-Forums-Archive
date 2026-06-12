---
title: "KINO not importing files"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by selfmade on 2006-09-02
i used a program in windows to change the format of some vidoes from my phone to .avi
i want to edit them in kino, but kino will not open them. any ideas?

---

### Post by brokenthorn on 2006-10-19
After 1 (one) day of trying to get to see why kino would not import I found a fix:
Edit /usr/share/kino/scripts/import/media.sh and where you see vstrict=-1, change the -1 to -2
It's apparently a small little bug in lavc... :/
OK then save the file and restart kino and open any avi file and kino will import it and convert it ffv1 video format which is in development and future versions of ffmpeg may not decode it.
Anyways it worked for me.

---

