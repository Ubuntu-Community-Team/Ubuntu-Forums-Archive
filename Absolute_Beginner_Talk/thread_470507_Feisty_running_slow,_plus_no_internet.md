---
title: "Feisty running slow, plus no internet"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by JewelledDragon13 on 2007-06-11
Problem 1.
I just installed Feisty dual-boot with Windows on a 3.2 GHz P4.  Fresh installation of both; Windows is not yet activated.  But Feisty is running ridiculously slow.  Half the time applications don't launch.  This gets worse the longer the machine has been on.  Note: I have experienced no such problems with Windows on the same computer.
Earlier it kept freezing and I thought it was probably overheating, so I took off the side and that solved it.  Could overheating make it run slow without freezing?  What else might be the problem and what can I do about it?

Problem 2.
I have a static IP and I can't access the internet.  I've tried all the obvious stuff (trying an IP that I know works from another computer, trying another computer in the same ethernet jack, etc etc), but nothing has made it work.  I can't access the internet through Windows either.
It's possible that it's just always timing out because Ubuntu is running so slow, but I doubt it, because I can't get internet from Windows either.  What might be the problem?

---

### Post by HackingYodel on 2007-06-11
Problem 1:

Sounds like your hardware may be the problem. 

How did you install Feisty to the computer, how much hard drive did you give it?  
How much memory does your computer have and how much can Feisty see? (type **free** in a terminal widow to find out)
Is Windows running slow on the machine now, also?

Problem 2:

How does this computer access the internet?  Modem, Network Interface Card, wireless, etc.?
How do you get your internet service?  DSL line, cable modem, dial up, etc.?
What other items are between this computer and the internet?  Network hubs, routers, cable/DSL modems?

Hopefully we can find you problems and get you on Ubuntu full time. :)

---

### Post by JewelledDragon13 on 2007-06-12
Thanks for the help...

1. I installed it from CD into about 25 gigs of free space I had left open for the purpose.  I've got 1 gig of RAM.  Ubuntu sees all of it.   Haven't messed around with Windows much yet because it's not activated, but it seemed OK.  

2. I'm going to ask the local IT folks about this, since it isn't just an Ubuntu problem.

---

### Post by SkyNet2029 on 2007-06-12
Can you please post the output of

```
$free
```

Also, what is the machine you are running on, and what kernel do you have running...

```
$uname -r
```
would list your kernel type that is currently running.

By 'It's running hot' , are you referring to the cpu itself, or is it just the hard drive? 

As much info as possible would be a solid starting point so others may provide more assistance to you.

I suppose the biggest question should be 'How many cores does that P4 of yours have?'

---

### Post by JewelledDragon13 on 2007-06-14
I got my local techies to look at it and it turned out to be all hardware problems (network card and hard drive), which I've gotten sorted out now.

---

