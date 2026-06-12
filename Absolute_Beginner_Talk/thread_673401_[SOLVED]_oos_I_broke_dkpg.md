---
title: "[SOLVED] oos I broke dkpg"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by smile_sunshine on 2008-01-20
Accidently kicked the off button on my computer midway through installing stuff with apt-get .


Now when i try to run apt-get it says 
> dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

when I try that it did set up some things but now just says 

> dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
Aborted



Please can I have some help to fix it?

Thanks

---

### Post by Nano Geek on 2008-01-20
Does **sudo aptitude -f install** do anything?

---

### Post by smile_sunshine on 2008-01-20
yes its working fine now, thanks so much :)

---

