---
title: "How to backup source.list"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-05-29
I would like to know how to backup source.list and where the backup should be stored.

I am curious if a backup is needed very often?

---

### Post by yabbadabbadont on 2007-05-29
In a terminal window run:
```
sudo cp /etc/apt/sources.list /path/to/directory/where/you/want/to/store/your/backup/sources.list.backup
```
Unless you often add and remove repositories to your sources.list, you probably only need one backup.

---

### Post by SoulinEther on 2007-05-29
You can just open up Nautilus, browse to /etc/apt/, right click on the file, copy, and paste it in any folder you own... like...

/home/youruser/backups/aptsources/

---

### Post by Inxsible on 2007-05-29
Open up a terminal and 

```

sudo cp /etc/apt/sources.list file /home/<your-username>/sources.backup

```

Simple !

---

### Post by yabbadabbadont on 2007-05-29
Operation Overkill is now complete...  :lol:

---

### Post by Ek0nomik on 2007-05-29
> **yabbadabbadont said:**
> Operation Overkill is now complete...  :lol:

Not quite:

All you have to do is type:

```
sudo cp /etc/apt/sources.list /path/to/directory/where/you/want/to/store/your/backup/sources.list.backup
```

;)

[CENTER]Bibliography[/CENTER]

yabbadabbadont.  May 29, 2007.  <http://ubuntuforums.org/showthread.php?t=457757>

---

### Post by ICUR2Ys on 2007-05-29
Thank you

I am so green that this is going to take me a few minutes to figure out and make the new directory create the backup there.

I really appreciate your help thank you.

---

### Post by yabbadabbadont on 2007-05-29
You should probably follow SoulinEther's solution as it is the easiest.

---

### Post by Ek0nomik on 2007-05-29
> **ICUR2Ys said:**
> Thank you

I am so green that this is going to take me a few minutes to figure out and make the new directory create the backup there.

I really appreciate your help thank you.

You can create a directory with the terminal if you wish quite easily:

```
cd /path/you/want/to/make/directory/in
mkdir folderNAME
```

---

### Post by yabbadabbadont on 2007-05-29
@Ek0nomik: You corrected your initial example just as I was quoting you so that I could correct it myself...  :D

Edit: OK, I was going to tease you a little too.  ;)

---

### Post by SoulinEther on 2007-05-29
The beauty of Linux is how many ways you can attack one problem.... and one way is not necessarily the superior.

---

### Post by ICUR2Ys on 2007-05-29
It took a couple of tries but I just checked and the backup is there.

Why did you refer to it as over kill?  I try to do things that I see on other threads sometimes they work most of the time I create problems.  On another thread someone screwed up his list following someones instructions.  Or at least trying to.

So I figure I could be next.

I really appreciate your help.  As sorry as I am now I was much worse a couple of weeks ago.

Really thanks.

---

### Post by Inxsible on 2007-05-29
you don't have to be sorry.

I think yabbadabbadont said "overkill" because in a space of 3 mins you had 3 similar replies except SoulinEther who gave a different method :)

---

### Post by SoulinEther on 2007-05-29
By overkill I think he meant 10 people came to answer the question all with the same or similar results.

Damn. Overkill again.

---

### Post by Ek0nomik on 2007-05-29
LOL yabbadabbadont.  I couldn't let you get away with it!  ;)

ICUR2Ys:  He meant because someone posted the exact solution as himself.  ;)

**EDIT**:  Wow, look above.  Great example.  :)

---

### Post by Inxsible on 2007-05-29
> **SoulinEther said:**
> By overkill I think he meant 10 people came to answer the question all with the same or similar results.

Damn. Overkill again.

Hee Hee :biggrin:

---

### Post by yabbadabbadont on 2007-05-29
What I meant was....  oh, never mind.  :lol:

(what they said)

---

### Post by ICUR2Ys on 2007-05-29
Thank you I thought it referred to what I wanted to do.

I appreciate everyones help.

---

