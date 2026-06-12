---
title: "more ipod trouble *sigh*"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by thesonisshining on 2007-06-06
so i tried to drag and drop a song to my ipod using rhythmbox (which by the way has worked every other time) and i get a warning that says

"error transfering track, no space left on resource"

i have a 1Gig. ipod shuffle and i'm only using 336.4 Mb.

what is the issue?

---

### Post by thesonisshining on 2007-06-06
any ideas people?...

---

### Post by Ek0nomik on 2007-06-06
error transfering track, no space left on resource

is that the *exact* error message?

---

### Post by thesonisshining on 2007-06-06
yes. word for word.

---

### Post by Ek0nomik on 2007-06-06
Sorry, I can't find anything relating to your problem.

Hopefully someone else will respond, or you can try other solutions using gtkpod or Amarok.

---

### Post by specs10 on 2007-06-06
if you've deleted some files off of it, check and see if a hidden trash folder has been created on your iPod.  I haven't used my old 3g ipod recently, but I know that it happens with all my other mass storage devices.

---

### Post by thesonisshining on 2007-06-06
*phew*

that was the problem thank you. i had checked the ipod control folder; but i had forgotten to check the base ipod folder itself.

---

### Post by specs10 on 2007-06-06
no problem.  happy to help  :)

---

### Post by mohansoundar on 2007-07-01
> **thesonisshining said:**
> *phew*

that was the problem thank you. i had checked the ipod control folder; but i had forgotten to check the base ipod folder itself.


I too face the same problem #-o
I did a du on the mounted directory ( /media/ipod ) and found that the directory size is very small ( 29 MB )
It has only the iPod_Control folder.  I have also.  Which one do you mention as ipod base folder ?

Could you please advise ?

17M     IPOD/iPod_Control/Music/f31
13M     IPOD/iPod_Control/Music/f10
4.0K    IPOD/iPod_Control/Music/f55
4.0K    IPOD/iPod_Control/Music/f32
4.0K    IPOD/iPod_Control/Music/f04
29M     IPOD/iPod_Control/Music
29M     IPOD/iPod_Control
29M     IPOD/


- Mohan

---

