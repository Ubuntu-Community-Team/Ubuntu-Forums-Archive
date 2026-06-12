---
title: "Yay I ditched Windows, now the nightmare lol"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by StarscreamUK on 2007-07-16
As my signature shows I've always been a Windows person.  After the debacle of paying a fortune for Vista Ultimate only to discover its the most buggy and unreliable piece of software I have ever had the misfortune to own, I decided to go Linux.

I've had a look through the forums and can't find anyone with the same problem as me though.

I have an ATIX1300 card, if I enabled the restricted drivers, my windows are missing bits.  If I drag an icon across the screen it vanishes, the terminal window is see through apart from where there is text.  I downloaded the latest ati drivers, but when i do sh etc it unpacks then deletes the temporary directory...... it doesnt run the installer as shown on the ati website.

Now I know I am a newbie to linux, but i'll struggle with it because I really don't want to go back to Micro$oft.

Cany anyone help me, or should i just try and get another cheap gfx card?

---

### Post by asmoore82 on 2007-07-16
Instead of settling for a cheap gfx card...
how does the system run with the ATI card and the default Free drivers?

---

### Post by StarscreamUK on 2007-07-16
I've just done a fresh install (its so easy and quick :) )

Using the default drivers, it runs fine, windows being dragged are a bit choppy, but at least they are complete and not see through or updating in only in some areas.

This is what I mean, this community tries to help.  Windows vista, pah.......

---

### Post by asmoore82 on 2007-07-18
the ATI nonFree drivers on my Laptop hand when I drop down to the
TTY [ctrl+alt+F1] and try to come back agan [alt+F7]
so I'm about to ditch the nonFree drivers too :D

---

### Post by Hobo Joe on 2007-07-18
In the terminal, type:
```

sudo aptitude install envy

```
Then select Envy from Applications > System tools > Envy. 
Select 'uninstall ATi driver', once that is done, select 'install ATi driver'. Make sure to let it configure your xorg file.

---

