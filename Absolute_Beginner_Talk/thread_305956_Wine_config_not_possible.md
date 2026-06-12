---
title: "Wine config not possible"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by mackyman on 2006-11-24
I did a fresh install on Edgy (couse when I upgraded, too much broke), and thought on installing wine again, and now I'm in some trouble.

I added the budgetdedicated.wine repositories to get the latest wine. And as I run wineprefixcreate or winecfg I get this error:

```
mackyman@mackycomp:~$ wineprefixcreate
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 000b), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
0000000c
        0000000d    0
0000000a
        0000000b    0
00000008 (D) (null)
        00000009    0
/home/mackyman/.wine updated successfully.
mackyman@mackycomp:~$ wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 000d), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
0000000c (D) (null)
        0000000d    0
0000000a
        0000000b    0
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) (null)
        0000000b    0

```

And then it does nothing more. I tried the normal ubuntu repostitories for wine, but the same happened there.

I really don't know where to start here. I have searched the forums for similar error, but found none.

I tried to start a program with wine without conf it, but no luck there (what else could I expect).

](*,)

---

### Post by cantormath on 2006-11-24
I would use [automatix2]("http://getautomatix.com") to install wine and then go from there.

I also use crossover office, which you could probably get off any torrent site.  It has a very nice wine configuration.

---

### Post by bodhi.zazen on 2006-11-24
> **mackyman said:**
> I did a fresh install on Edgy (couse when I upgraded, too much broke), and thought on installing wine again, and now I'm in some trouble.

I added the budgetdedicated.wine repositories to get the latest wine. And as I run wineprefixcreate or winecfg I get this error:

And then it does nothing more. I tried the normal ubuntu repostitories for wine, but the same happened there.

I really don't know where to start here. I have searched the forums for similar error, but found none.

I tried to start a program with wine without conf it, but no luck there (what else could I expect).

](*,)

Try [downgrading wine](http://doc.gwos.org/index.php/HowToWine#Downgrade_wine).

I would try as far back as 0.9.18 or so.

Otherwise check in with [wineHQ](http://www.winehq.com/).

---

### Post by mackyman on 2006-11-24
> **bodhi.zazen said:**
> Try [downgrading wine](http://doc.gwos.org/index.php/HowToWine#Downgrade_wine).

I would try as far back as 0.9.18 or so.

Otherwise check in with [wineHQ](http://www.winehq.com/).

That did the trick =) Thanks!

Now I just have to find wich of the latest wine versions that works with my machine. Hopefully I will get my program to work properly.

> **cantormath said:**
> 
I also use crossover office, which you could probably get off any torrent site. It has a very nice wine configuration.

I swiched to linux to get rid of these solutions. No more unbought copies of software. And besides, it's for a company in the future, where all software have to be completly legal.

But thanks anyway for the tip.

---

