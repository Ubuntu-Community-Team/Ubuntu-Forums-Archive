---
title: "Cammand to look up specs of computer"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-26
What cammand can I use to see how much ram I have or what my proccessor speed is?

---

### Post by scxtt on 2006-06-26
CPU:
cat /proc/cpuinfo

MEMORY:
cat /proc/meminfo

---

### Post by WADemosthenes on 2006-06-26
using: cat /proc/meminfo, is "total memory" the RAM?

---

### Post by tonyr on 2006-06-26
Install package **hwinfo**, then
```

hwinfo > hwinfo.log

```

Examine the file hwinfo.log for more info about your machine that you could ever possibly 
want to know.

---

### Post by scxtt on 2006-06-26
[QUOTE=WADemosthenes]using: cat /proc/meminfo, is "total memory" the RAM?[/QUOTE]yes, the 1st line is the total amount of ram in your system, the rest is how it's being used ...

---

### Post by WADemosthenes on 2006-06-26
[QUOTE=tonyr]Install package **hwinfo**, then
```

hwinfo > hwinfo.log

```

Examine the file hwinfo.log for more info about your machine that you could ever possibly 
want to know.[/QUOTE]

I don't have the internet yet so I can't install packages :(, I just put in some new ram, and I wanted to know how to see if it was working.  Is there anyway to just look at how much ram the computer is detecting?  I tried in BIO's and couldn't find it.

---

### Post by tonyr on 2006-06-26
In a terminal do
```

grep LOWMEM /var/log/messages*

```

You should see a bunch of lines. some showing the old memory size, some the new (if I'm
guessing right).

---

### Post by WADemosthenes on 2006-06-27
[QUOTE=scxtt]yes, the 1st line is the total amount of ram in your system, the rest is how it's being used ...[/QUOTE]

I have a 128 mb stick of RAM, and added a 64 mb of RAM (I'll take what I can get :P) but it seems to think that I only hav 175 mb of RAM altogether (the boot up screen tells me how much RAM I have too, it says 191 :D).  Interesting, will it affect preformance?

---

### Post by Ozitraveller on 2006-06-28
HardInfo I think is in universe. Buit it's only ver 0.3.7pre-2, 0.4.1 isn't in the repos yet.

[http://hardinfo.berlios.de/wiki/index.php/Main_Page](http://hardinfo.berlios.de/wiki/index.php/Main_Page)

---

