---
title: "Installing dual-boot"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by bobmorris on 2006-09-01
I've RTFM'ed the docs on installing Ubuntu as a dual-boot, and have a couple of questions.

I'd like to install it on an XP Home box that has one hd with four logical partitions (C,D,E,F.) Any problem with this many partitions?

If I install it in the non-manual mode, the first option, will it take all available hd space, just some or what? I don't want it to take all additional space but am not comfortable using manual mode.

Any help appreciated.

(My Ubuntu laptop arrives soon, and currently I'm running the Live CD, Ubuntu is wonderful...)

---

### Post by squell on 2006-09-01
what I would do is move data from the F drive to C/D/E.  Then in Ubuntu use a manual partition setup and format this empty drive and in there put your "/" (root) and "swap" drives.

It really depends how much room you wanna donate to ubuntu.

---

### Post by Ambimom on 2006-09-01
It's very simple.  When you load the CD, there's an install icon on the desktop.  When you click on that, it will walk you through the partitioning.  It won't refer to the CDEF as it does in Windows.  Linux has its own terminology: hda. 

An easy way to remember what is what is by the size of the partition.  That's how I did it, but you can also look at this video: [http://enterprise.linux.com/article.pl?sid=06/07/05/1533204&from=rss](http://enterprise.linux.com/article.pl?sid=06/07/05/1533204&from=rss) which shows you step by step.

There are plenty of failsafes in case you're not sure.  It will ask you several times whether it is ready to go forward.   It's pretty straightforward.  

Good luck.

---

### Post by MiCovran on 2006-09-01
My advice is partiton manually. It's not complicated and you can set up your hard drive as you want it.

---

### Post by aysiu on 2006-09-01
> **MiCovran said:**
> My advice is partiton manually. It's not complicated and you can set up your hard drive as you want it.
Ditto on that.

When you read the f'in manual, which did you read? I hope it was one of these:

**Desktop CD**:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

**Alternate CD**:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by bobmorris on 2006-09-01
Thx for the help all, I'll try the the manual process after reading  up more on it.

---

### Post by bobmorris on 2006-09-02
Some final questions.

The computer has 25gb free on C: out of 40gb: and F: is empty, with 15gb

1) If I use option 1, resize hda1, does that mean it will take unused space from C: only? If so, will it take all available unused space or just some  of it?

2) If I install on F:, I put / and swap there, then mount C, D, and E with no reformat, calling them something like WINC, WIND, WINE?

Do I have it right?

---

