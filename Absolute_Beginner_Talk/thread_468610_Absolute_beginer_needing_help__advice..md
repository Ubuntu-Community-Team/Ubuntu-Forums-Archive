---
title: "Absolute beginer needing help / advice."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by DeuceII on 2007-06-09
Hi All,

I am a complete noob to Linux and have managed to set up a dual boot of Feisty on a spare PC to do all my learning.

I have encountered a problem and have no idea how to resolve.:

I was trying to instal some codecs so that I can view my .vob files from across on my Windoze network (which worked out of the box so to speak), and I managed to find what I was looking for and using add/remove tried to install them.

The following error came up in a dialogue box-

E:dpkg was interupted you must manually run 'dpkg--configure-a' to correct.
E:_cache->open()failed please report.

Now I haven't a clue what that means, so I thought ahh type the dpkg bit into a terminal, but the terminal reports that it isn't a proper command.

Now to add to that, I get the same error message when trying to install system updates that have downloaded.

Any help for me would be graciously accepted.

many thanks

DeuceII

---

### Post by killaray on 2007-06-09
i believ u type ```
sudo dpkg --configure -a
```
in terminal... try that im also pretty new to linux

---

### Post by DeuceII on 2007-06-09
> **killaray said:**
> i believ u type ```
sudo dpkg --configure -a
```
in terminal... try that im also pretty new to linux

That worked a treat, thank you very much.

Peace be with you

DeuceII

---

### Post by killaray on 2007-06-09
np... happy i could help someone

---

