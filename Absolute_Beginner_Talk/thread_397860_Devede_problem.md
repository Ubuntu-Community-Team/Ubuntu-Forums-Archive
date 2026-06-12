---
title: "Devede problem"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-03-31
Hi again, been messing around with Ubuntu on my own time these past few weeks and becoming very interested. In my search for a replacement to my nero program I found Devede which is a very nice DVD authoring program and seems to do exactly what I need which is make traditional dvd movies for regular DVD playback. Anyway my problem is that when I try to burn the ISO output I get from the program I get this message, I tried two seperate ISOs of the same project and I'm now trying a different project but I don't think it has to do with the media I converted itself. I used gnomebaker's ISO burning to do that.

```
Executing 'builtin_dd if=/media/hda6/movie.iso of=/dev/hdc obs=32k seek=0'
:-( write failed: Input/output error
```

Anyone had this error? I know my drive works and gnomebaker works on its own since I've burned plenty of data DVDs in the past week... hope someone can help, thanks :)

---

### Post by halitech on 2007-03-31
Have you tried using K3B to burn the ISO? I use Devede all the time and burn using K3B and I've never seen the error (or maybe I'm just lucky)

---

### Post by arron on 2007-03-31
Just to cover some basics tobe sure, its a blank cd in the drive?  is there mor than 1 cd rom, is hdc your dvd burner? is /media/hda6/movie.iso where its saved (can you browse to that folder and see the file there?)?

---

### Post by starcraft.man on 2007-03-31
It seems very weird... I just burned two other DVD movies with the program and they worked fine... would appear there must be some error with the actual file though I'm not sure why. Is there a program I can use to check the integrity of my vid file?

---

### Post by mondomunchies on 2008-06-04
I know this is an old thread but I just came across the same problem and somehow got it to work:

Alright this may not help you. I had the same problem. Trying to burn the iso with brasero it would "erase dvd" like normal (because i'm using dvd rw) and just as its about to burn it gives me the same error you got. I did this to fix it (and i dont know how it worked)

Put in a different and blank dvd r or rw, wait for the blank disc to appear on your desktop. then double click on the iso and burn it. thats it.

---

