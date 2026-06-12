---
title: "Security software"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by Rich3077 on 2006-07-31
Okay I did post this first request in the everlasting "New to Linux? Need a program?"  thread and havent received a responce yet. I would like a firewall program that would alert me anytime a program tried to access the internet on its own or "phone Home" with the added abilty to block such requests. 

2nd program I would like is a file shredder to stop recovery of hard drive files. A huge bonus if it allows all files deleted from the trash bin to be shredded, as well as shredding free disk space. 


Anyone know if such programs exist?

Peace
Rich

---

### Post by T700 on 2006-07-31
The [shred]("http://linux.about.com/library/cmd/blcmdl1_shred.htm") command, although there is some question if it is effective on journaled file systems.

You can use the built in firewall in Linux and configure it with Firestarter or Guard Dog (both available from the repositories).  Set a rule to block all out bound traffic and alert you.  As programs request access, you can grant or deny them.

Paul

---

