---
title: "[SOLVED] rosegarden error"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by lolzlolz on 2008-02-23
i have a problem where when i start rosegarden it says that the system timer resolution is too low Rosegarden was unable to find a high-resolution timing source for midi performance
how can i get this to stop so rosegarden will work?
thanks

---

### Post by A4006 on 2008-02-23
Yeah, I have the same error.

---

### Post by lolzlolz on 2008-02-24
do u have any idea how to fix it?

---

### Post by A4006 on 2008-02-24
Unfortunately, no.

---

### Post by lolzlolz on 2008-02-24
ive read some stuff about recompiling the kernel, what's all thsi about, i cant seem to figure out how

---

### Post by lolzlolz on 2008-02-25
bump

---

### Post by A4006 on 2008-02-25
I confess I have no clue what to do.. I was just expressing my interest in seeing what the answer is... so...

---

### Post by mkoehler on 2008-02-25
You have to run your kernel in real-time mode.  This isn't exactly an easy process to do...you can start by going into synaptic and downloading a real-time kernel.  From there, you have to modify configuration settings in text files to allow programs to be operated in real-time, then restart into the new kernel (from GRUB).  Obviously, this is just an overview, but that is what you need to do.

---

### Post by lolzlolz on 2008-02-29
does anyone have more info or exact steps on how to do all this?
thanks

---

### Post by lolzlolz on 2008-02-29
nvm i got it working easy, go into synaptic and search realtime
once there select all the packages that are linux-rt or something that has linux in its name
then install, you will have to restart then rosegarden will work :guitar:
also no extra configuration of anything is required all my programs still work after i do this including games, gimp, etc
so no configuration except this is needed
thanks

---

