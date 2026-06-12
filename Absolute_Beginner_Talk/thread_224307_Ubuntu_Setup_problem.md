---
title: "Ubuntu Setup problem"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by manosone on 2006-07-27
Hello all.I have a problem with the 6.06.I am trying to set it up on a p3 600mhz pc with 348ram.This pc was running win xp.The problem is that,after the screen that says "loading essential drivers etc" it goes on to the next screen and it says"uncompressing linux...ok,booting  kernel",and it stays there.It does not freeze,but it is not going further.I just burn this dvd,and ihave also tried it on another pc and it worked.Also i boot from the live cd 5.10 and it worked too.Any ideas?

---

### Post by Chuck_W on 2006-07-27
I had a similar problem on a P III 800 a while back. It had on board video that was flaky so I put a PCI video card in that worked on Windows. The problem was that Ubuntu 5.1 couldn't get past the on board video. I ended up taking the card out and living with the crappy video until I replaced the machine. If that is your problem you will probably have to run:

dpkg-reconfigure -phigh xserver-xorg

to get the video set up. once you do that type:

init2

to startgnome or whatever you are using.

hth

---

### Post by cmo220 on 2006-07-27
I had the same problem, for me it was the monitor I was using.  I tried everything, wouldn't work.  Then I decided to try another monitor and it worked fine.

---

### Post by molly_001 on 2006-07-27
manosone --
For a very older machine, you'll have more success doing the install using the Alternate Install CD for Ubuntu 6.06 (instead of the Live-CD).  I can't tell which you were attempting to use, but just in case...

---

