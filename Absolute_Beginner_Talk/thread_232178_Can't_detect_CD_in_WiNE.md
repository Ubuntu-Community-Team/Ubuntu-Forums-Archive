---
title: "Can't detect CD in WiNE"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by IceT on 2006-08-08
Hi all, 
I'm having trouble with WiNE about changing cds. I'm trying to run EyeQ iso, i mounted the iso, ran the installer, everything is working great, except when i lauch the program, it keeps telling me to insert the cd, and there's no way to change the path or anything. 
Anyone had a similar situation?
thanks

---

### Post by davebgimp on 2006-08-08
EyeQ...you mean this?
[http://www.infmind.com/](http://www.infmind.com/)

If so, It seems like they sell only CDs, so is there a reason you're using an ISO?

---

### Post by IceT on 2006-08-08
Ya it's that Informind EyeQ
I installed it from the cd the first time, but i read in another post that these guys wanted to instal a simpson game with 3 cds, they had to make the cds into iso and mount them to different mount points jsut so they can swap cds. but that didn't work for me.

---

### Post by IceT on 2006-08-08
I actually had the same setup in my windows partition, because i didn't want to have the program read from cd all the time, so i made and installed from the iso and kept the iso mounted all the time, and it always worked fine

---

### Post by davebgimp on 2006-08-08
Hmm, I'm not having much luck... but here's an idea...a guess really. Try mounting the ISO, then running 'winecfg' from a terminal. I'm wondering if perhaps wine will then see that ISO as a CD? Then, maybe try running the installation again. I could be totally off about this, but it wouldn't hurt to try.

---

### Post by IceT on 2006-08-08
nice nice.. that winecfg was all i needed :P
i added a drive mount point to the drives section, and it worked!
thanks so much

---

### Post by davebgimp on 2006-08-08
Holy crap! I was right! Wooo!

Anyway, you may later want to run 'winecfg' again with the ISO unmounted if you no longer need it...just to clear that virtual drive from wine.

Glad to help.

---

### Post by my_key on 2007-06-09
Thanks for the tip. I wanted to know if the program would run in wine. Guess it does. And now I know about winecfg in advance :D

---

