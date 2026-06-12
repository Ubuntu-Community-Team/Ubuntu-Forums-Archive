---
title: "how to create shortcut to a folder?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by qdvubun on 2006-07-20
how to create shortcut to a folder in /media/share on the desktop?

---

### Post by PriceChild on 2006-07-20
From the man page:
> LN(1)                            User Commands                           LN(1)

NAME
       ln - make links between files

SYNOPSIS
       ln [OPTION]... [-T] TARGET LINK_NAME   (1st form)
       ln [OPTION]... TARGET                  (2nd form)
       ln [OPTION]... TARGET... DIRECTORY     (3rd form)
       ln [OPTION]... -t DIRECTORY TARGET...  (4th form)

DESCRIPTION
       In  the  1st form, create a link to TARGET with the name LINK_NAME.  In
       the 2nd form, create a link to TARGET in the current directory.  In the
       3rd  and  4th  forms, create links to each TARGET in DIRECTORY.  Create
       hard links by default, symbolic links with --symbolic.   When  creating
       hard links, each TARGET must exist.
So basically:

```
ln /media/share ~/Desktop
```

---

### Post by shanepardue on 2006-07-20
is that the only way to do that?

no way through the gui?

---

### Post by monkieie on 2006-07-20
> **shanepardue said:**
> is that the only way to do that?

no way through the gui?

are you using Ubuntu? I did this myself for the first time today and it's dead easy. So easy in fact that I can't tell you off the top of my head how to go about it #-o 

I'm not on my linux machine at the mo (I'm at work) so...

if you wait until tomorrow I'll be able to give you the solution to this, but I would imagine that somebody else will have provided the answer before then ;)

---

### Post by PriceChild on 2006-07-20
You can do it through the gui yes by "middle click dragging" a folder you want to link to the place you want it linked.

Pricey

---

### Post by shanepardue on 2006-07-20
ohh that's very nice!!

---

### Post by spier on 2006-07-20
> **shanepardue said:**
> is that the only way to do that?

no way through the gui?

From within nautilus, drag folder with mouse middle button and drop it on desktop!

Oops, to lazy! Glad PriceChild pointed it out!

---

### Post by qdvubun on 2006-07-20
ohh!! tricky little middle button!
thank you.

---

### Post by justicerulesok on 2006-07-25
Thanks for this I was trying to figure it out & did a search.  I thought I'd let you know these forums really do work!

Justice.

---

### Post by johnwillis on 2008-06-29
> **PriceChild said:**
> You can do it through the gui yes by "middle click dragging" a folder you want to link to the place you want it linked.

Pricey

Thanks so much. That has saved loads of time in the terminal :)

Cheers!

---

### Post by jbaerbock on 2008-06-30
Why do some people respond in terminal commands all the time? Lol come one people give the easiest solution aka GUI!

---

