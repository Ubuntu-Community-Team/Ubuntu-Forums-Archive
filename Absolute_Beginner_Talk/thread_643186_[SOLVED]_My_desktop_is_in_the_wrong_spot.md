---
title: "[SOLVED] My desktop is in the wrong spot"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by jerome1232 on 2007-12-17
Ok so I had AMD64 version of ubuntu 7.10 and decided to change over to i386 version for compatibility reasons, well i backed up my /home directory reformated etc...

on my nice shiny new install I copied my old home directory back over and now my desktop is in /home/jeremy/.trash/Desktop     if i empty the trash it will kill all my icons on the desktop, then the Desktop folder will get recreated there, how can i tell ubuntu to put my desktop back at /home/jeremy/Desktop ?? i just accidently wiped out a bunch of files on my desktop when i cleared my trash then watched my icons go bye bye then I started investigating it.

---

### Post by LaRoza on 2007-12-17
Can't you just copy it back?

---

### Post by SOULRiDER on 2007-12-17
just do a 
```
move ~/.trash ~/Desktop
```

I think that shoudl work, but backup everything again just in case :P

---

