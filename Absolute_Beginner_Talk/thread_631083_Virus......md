---
title: "Virus....."
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by old_dog on 2007-12-04
I have been told there are two Linux viruses/viri out there.....true/false.

As I have banged on about how virus free Ubuntu is are they winding me up out of malice!
Should I install anti virus stuff, what should I install and how?

All the Best
old_dog

---

### Post by hyper_ch on 2007-12-04
> **old_dog said:**
> I have been told there are two Linux viruses/viri out there.....true/false.
More like 30 viruses

> **old_dog said:**
> As I have banged on about how virus free Ubuntu is are they winding me up out of malice!
30 viruses compared to 60k on windows is pretty muc virus free ;)

> **old_dog said:**
> Should I install anti virus stuff, what should I install and how?
No need to, the viruses for linux are more proof-of-concept than dangerous and it's very hard to catch them if you get all your software from trusted sources.

---

### Post by PmDematagoda on 2007-12-04
The viruses are also not really effective and cannot spread efficiently, so basically it is assumed that there are no viruses.

But that is no reason to drop everything about security, you do need to be careful about stuff like root kits. And if you are really careless, you just might have the opportunity of getting some Linux viruses on your PC;).

---

### Post by bodhi.zazen on 2007-12-04
Linux security is different then Windows security. Take a look at this :

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by skymera on 2007-12-04
plus if you do get a virus, it cant touch your system, just your home.

unlress you run as root, then well, your stuffed :wink:

just be careful what you execute.

---

### Post by GSF1200S on 2007-12-04
> **bodhi.zazen said:**
> Linux security is different then Windows security. Take a look at this :

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

You are EVIL! I got lost clicking all over the place for a half hour.. :)

Good stuff to know...

---

### Post by quandary on 2007-12-04
> **hyper_ch said:**
> 
 if you get all your software from trusted sources.


Yes, that's exactly the point: if.
But I do not only use trusted sources. In fact, I'm inclined to highly distrust some of my sources...

---

### Post by erginemr on 2007-12-04
> **old_dog said:**
> I have been told there are two Linux viruses/viri out there.....true/false.

As I have banged on about how virus free Ubuntu is are they winding me up out of malice!
Should I install anti virus stuff, what should I install and how?

All the Best
old_dog

Hello,

The following is a good read:
[http://www.whylinuxisbetter.net/items/viruses/index.php](http://www.whylinuxisbetter.net/items/viruses/index.php)

You definitely do not need an antivirus under Linux, but one may come in handy if you are planning to use Wine emulator to run Windows programs or are dual-booting and often download Windows programs from under Linux to check them if they are virus-free.

I have read somewhere there are some 40 - 50 virii written for Linux and most of them have been written by Linux developers themselves to test its security. 

Root kits, however are anoter story:
[http://en.wikipedia.org/wiki/Rootkit](http://en.wikipedia.org/wiki/Rootkit)

It is highly unlikely that a regular Linux user will be affected by a rootkit, but if you feel like paranoid, you can install "Rootkit Hunter" or "Check Rootkit" with:

```
sudo aptitude install rkhunter
sudo aptitude install chkrootkit
```

and run it at regular intervals to feel safe.

---

### Post by fatality_uk on 2007-12-04
> **old_dog said:**
> I have been told there are two Linux viruses/viri out there.....true/false.

As I have banged on about how virus free Ubuntu is are they winding me up out of malice!
Should I install anti virus stuff, what should I install and how?

All the Best
old_dog

Nice replays so far guys!! As I understand it, there are no reported "wild" viruses for Linux. However there ARE Linux viruses, but mostly technical exercises. The biggest reason is IMHO, that Linux is Open Source.

As I have posted before, owning a Linux box shouldn't mean you don't think about security. I was mostly thinking of a multi-user home/work environment. Exploits less, but because an infected binary file can sit of your Linux workstation without "you" having to worry, if that file is then used by an MS user, that could cause a problem. Ignoring the "well they should change to Linux and they wouldn't have to worry, morons" argument, I would say that if you do work with and exchange files with MS users, the basic security steps should be applied.

By the way, are you a member of ScunDogs by any chance?

---

### Post by old_dog on 2007-12-06
Thanks for your replies guys.......
I think I can carry on boring all and sundry about the superiority of Linux and Ubuntu with a clear conscience.
I have never heard of Scundogs.....Give us a clue
Cheers Old_dog

---

