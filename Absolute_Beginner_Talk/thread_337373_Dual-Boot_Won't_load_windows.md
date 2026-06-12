---
title: "Dual-Boot Won't load windows"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Cairna on 2007-01-12
Now, I had posted a problem with my dual-booting, but since that is resolved I figured I should post a new topic for new problems.

I had posted about my problem in the old thread but I thought maybe I should make a new one for a specific and rather different problem, sorry if I was wrong in doing so.

So, I created my partitions a linux ext 2, it's swap while keeping my recovery partition and my main Windows Xp Partition.

Now my problem is that after a lot of troubleshooting with Norton Partition Magic I have finally managed to get my hard drive partitionned and my system installed. 

However, to connect myself to the internet I noticed that I had to go get some drivers, I figured " Hey, no problem" and rebooted. Unfortunetely I now get the error before window can load that

xmnt2002 Cannot be found- Autocheck Will not Start
autochk Cannot be found- Autocheck Will not Star

After that, the computer restarts promptly and so my only option is to go into Ubuntu. I had heard that perhaps my problem had been that the information from those two partitions had been mounted into my linux partition, which should not be.

So at this time, I have all my files from Windows XP on my ubuntu setup ( as well as the Compaq Presario Recovery System ).

My question is this, what is the least destructive way to get both my Ubuntu ( currently working ) and windows XP both working functionally?

Is there any way for me to get my old windows files *back* into the NTFS partition?

---

### Post by Cairna on 2007-01-12
Sort of a breakthrough here, I found this link with people who had a similiar problem : 

[http://www.linuxquestions.org/questions/showthread.php?t=66137&page=2](http://www.linuxquestions.org/questions/showthread.php?t=66137&page=2)

 Apparently their problem was that it needed to be unhidden. I tried this which gave me a new problem, when I go to terminal and type in "cfdisk" it says that it cannot access drives...

---

### Post by rccharles on 2007-01-13
> **Cairna said:**
> Sort of a breakthrough here, I found this link with people who had a similiar problem : 

[http://www.linuxquestions.org/questions/showthread.php?t=66137&page=2](http://www.linuxquestions.org/questions/showthread.php?t=66137&page=2)

 Apparently their problem was that it needed to be unhidden. I tried this which gave me a new problem, when I go to terminal and type in "cfdisk" it says that it cannot access drives...

Might try the command:

gksudo gparted

One of the partitioning tools has on option to unhide  a partition.

Robert

---

