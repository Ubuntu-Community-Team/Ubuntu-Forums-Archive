---
title: "Minimize window closes it"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Techpenguin on 2007-12-31
Hi everybody. I just today upgraded to gutsy, and everything was workiong fine until I realized when I click the minimize button on a window it closes. if you have a solution please post it.:confused:

---

### Post by kd7swh on 2007-12-31
What window manager are you using?

If you are using compiz it maybe a different solution than if you are just using metacity.

you could try removing metacity altogether and reinstalling it.

Make sure you do a complete removal though so you purge the settings.

```
sudo apt-get purge metacity

```
then
```
sudo apt-get install metacity
```

may do the trick.

---

### Post by Techpenguin on 2007-12-31
thanks, i will attempt that now

---

### Post by Techpenguin on 2007-12-31
i tried the first one and this popped up; 
E: Invalid operation purge

---

### Post by staticvoid on 2007-12-31
try from synaptic, "complete removal"

---

### Post by eternicode on 2007-12-31
> **Techpenguin said:**
> i tried the first one and this popped up; 
E: Invalid operation purge

"purge" is an aptitude command.

```
sudo aptitude purge metacity
```

I believe the apt-get equivalent is

```
sudo apt-get remove --purge metacity
```

---

### Post by Ljbpfc on 2008-01-01
I'm using Compiz any solutions please help 

Thanks

---

### Post by kd7swh on 2008-01-02
a complete remove is the same as a purge so by all means if that works use it.

as for compiz it maybe related to the skin (in emerald) that you are using. you can reinstall compiz in synaptic and see if that resolves your issue or you may try playing with some settings in the emerald theme manager. 

good luck to you both.

---

### Post by CatKiller on 2008-01-02
> **Techpenguin said:**
> Hi everybody. I just today upgraded to gutsy, and everything was workiong fine until I realized when I click the minimize button on a window it closes. if you have a solution please post it.:confused:

Are you sure that the windows are actually closing, and you haven't just removed your Window List from the panel by mistake instead?

---

### Post by Ljbpfc on 2008-01-02
Thanks all for your rsponses but it was just i deleted my window list by accident (feel like a dumba** now) 










Thanks

---

### Post by crjackson on 2008-01-02
Don't feel bad, I've done it and so have many others too... :)

---

### Post by Michl on 2008-02-19
> **CatKiller said:**
> Are you sure that the windows are actually closing, and you haven't just removed your Window List from the panel by mistake instead?

I'm not sure what this means.  I click on the minimize icon and the window and application
closes and it is nowhere to be found.  I try minimizing with Alt+F9 and the same
thing happens. 

Trying to restore hidden windows does not show the closed window
because the application has also closed.

Add:
I see now.  Windows List is something one can add to the panel and it does the
trick.  There is still a mystery though.  In Dapper, Feisty and Gutsy this feature
was a default because I had no idea there was a Windows List and never
added it to the panel.  I guess after the most recent update in Hardy this was
not a default.    ...I think it should be a default....IMHO

---

