---
title: "everything really sluggish at the moment"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2008-03-22
i'm finding my system running quite sluggishly at the moment.

i've got 1gb of ram, a 3.33mhz processor and 100gb free on my 160gb hard drive (not that that makes a huge difference :D).

is there anything i can run for general maintenance or to try and identify anything running that shouldn't be ?

i've done a ps -fea on the console and the process all seem to be necessary - nothing seems untoward.

the best comparison is if you're on windows, it's like you've got a few spyware programs running in the background - it just doesn't feel right.

---

### Post by marco123 on 2008-03-22
Which version of Ubuntu are you running.  If your using Gutsy you could try turning off the file indexing service.  That tends to use cpu cycles in the backround.  

Other than that try restarting X : Ctrl>Alt>Backspace and see if that helps?

Also try running the "top" command in the Terminal to see what is eating the cpu cycles.  Press K then enter the PID of the process you want to kill if you need to.

Cheers, Marco.

---

