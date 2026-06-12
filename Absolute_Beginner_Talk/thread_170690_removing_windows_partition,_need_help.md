---
title: "removing windows partition, need help"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by meatball117 on 2006-05-05
Hello, 

I've been a Windows user for years, and over that course of time I've accumulated quite the collection of music. This being said, I would like to migrate completely to Ubuntu. 

Here's my problem.  Over the course of years I scattered all my music files all over my computer, and I'm sure there's an easy way to get linux to look and recursively copy all my music off my ntfs drive onto my shiny new ubuntu drive.  

I've tried cp, but it doesn't seem to want to delve into the directories, even with the -r tag on it. I"m sure i'm not using the right commands, but if anyone can help me out that'd be greatly appreciated!

-Wes

---

### Post by Sef on 2006-05-05
Look at Trinity Rescue Kit.

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

### Post by meatball117 on 2006-05-05
Hello again, I've looked over this program and I'm not sure this is what I want.. it looks to be just a loaded knoppix boot disk.  There's nothing I can use that recursively searches directories and just copies files over with a command? My linux boot is working just fine. :p

---

### Post by aysiu on 2006-05-05
I'm going to assume you have your Windows partition mounted. If not, follow these instructions: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

After that, just go to Places > Search for Files or KMenu > Find Files/Folders and do a search in the Windows mounted directory for ```
*.mp3, *.ogg
``` or whatever format you use. Highlight and cut and paste all the results to wherever you want them.

---

