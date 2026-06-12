---
title: "VAIO Laptop with Mobility Radeon"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by BHelts on 2007-06-21
ok..... i received a VAIO laptop second hand.  i have ubuntu on two other laptops and my desktop but i have never done one with an ATI video card.  This particular one is an ATI Mobility Radeon 9700/9200 (as stated in windows).  when i try to run the feisty LiveCD, i get garbled video.  i can run the LiveCD in safe graphics mode however.  What do I need to do to get the correct drivers installed so that i can get this guy up and running.

it will be exclusively Ubuntu when I am reasonably confident i can get it up and running.

i know there is a lot of information here on ATI video cards, but that was the problem, my searches were overwhelming.  if someone can point me in the right direction or help me out directly, i'd really appreciate it.

Thanks

---

### Post by Happy_Man on 2007-06-21
I guess start with fglrx and go from there.... generally, though, the 9200 is well supported.

---

### Post by BHelts on 2007-06-21
ok, so when i install feisty, if i have a problem with graphical login, should i ctl-alt-F1 to terminal and then do a ```
sudo aptitude install fglrx
``` or do i need to compile the driver into the kernel?

---

### Post by Happy_Man on 2007-06-21
Yep, one single command..... only it's xorg-driver-fglrx, not just fglrx.

---

### Post by BHelts on 2007-06-21
you're awesome.  thanks a lot for your help.  i'm going to give that a run when i get into work.

---

