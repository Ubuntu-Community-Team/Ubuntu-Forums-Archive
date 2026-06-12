---
title: "high memory usage problem"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by GeneticFlea on 2007-11-29
hey guys! im currently running 7.10 here and ive encountered an odd problem today. Things have started running very very slow on my comp, taking forever for things to load, sometimes the mouse stuttering etc. Checking my system monitor it says that my computer is running at 100 percent memory usage and 100 percent of the swap file. Now im running a amd 2500, 1gb of ram ,256 ati x800, so i dont think it should be that much of a problem, especially as im now running nothing intensive, i even shut down emerald which for some reason said it was using 4.0 gb of memory, but it hasnt helped at all. 

any suggestions? this is pretty ridiculous and im considering reinstalling. it takes forever to do anything on this computer and it sounds like its constantly processing, running the harddrives etc pretty hard, as if i was attempting some serious computing when all im doing is surfing the web. thanks!

---

### Post by vikramsharma on 2007-11-29
You can find out which app is causing this memory problem, I had a similar issue (was more of desktop freezing) on the new aluminum iMac 24" caused by bad ATI driver.  You can use top or ps -aux to find out the memory hogging app.

---

### Post by GeneticFlea on 2007-11-29
thanks for the reply! but what are those programs? ive never heard of either.

---

### Post by civic_si on 2007-11-29
top is a program that shows processor and memory usage in real time. and ps -aux will show close to the same but not in real time.

you can read the man page for them to see what all they do.

---

