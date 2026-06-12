---
title: "[SOLVED] End processes manually"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by mdewet on 2008-01-25
After installing gxine from a repo dvd, i ran the application.  There were few errors and codecs missing and whatnot, but the main problem came afterwards when I closed the application and, when I tried opening the cd-rom tray, recieved an error that said that an application (gxine) was preventing me from ejecting the disc.  I had to restart the session to fix that.  
Is it possible that gxine did not completely close down and still ran in the background?   
How can I manually kill a process, is there some sort of TaskManager in Gutsy?

---

### Post by Lord Illidan on 2008-01-25
There is one. It's in System -> Administration -> TaskManager.

You can also use the console.

eg : ```
killall gxine
```

---

### Post by jeffus_il on 2008-01-25
In a program called Process Manager, you can right click on a process and choose "kill". You can also see if it is running and also learn about your system, seeing which processes are running. It's good to be aware of the little bytes running around your CPU and occupying your memory.

---

### Post by CJ56 on 2008-01-25
On my system (Gutsy 7.10) it seems to live in System/Administration/System Monitor

Open the System Monitor

Click the Processes tab

Locate the running application under Process Name

Right-click it & tell it to end 

Hope this helps...

---

### Post by philinux on 2008-01-25
System>Admin>System Monitor.

Then select the processes tab, highlight the process right click select the option you need.

---

### Post by mdewet on 2008-01-25
Thanks for all the replies, it suddenly seems like a stupid question, it's actually quite easy..looking forward to learn Gutsy:guitar:

---

