---
title: "Installing KDE"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Gleep on 2007-06-07
I went on synaptic, and marked kde for install... when I clicked apply it says 

'please insert the disc labeled: ubuntu 7.04 _Feisty Fawn_ -Release i386 (20070415) in drive /cdrom/'

So I take it it needs to use the disc to install things... I used the alternate disc to upgrade from edgy to feisty, so will this do if I put that in?

Or is there another way which does not require a disc?

Thanks =]

---

### Post by sandwitch on 2007-06-07
there are some lines at the top of your /etc/apt/sources.list about cdrom
comment them do apt-get update and your up and running

---

### Post by Gleep on 2007-06-07
> **sandwitch said:**
> there are some lines at the top of your /etc/apt/sources.list about cdrom
comment them do apt-get update and your up and runningUnfortunately I find that most confusing... I'm not sure what you're trying to tell me to do here... thansk for the response though.

---

### Post by sandwitch on 2007-06-08
The above is an answr to this question "Or is there another way which does not require a disc?"

---

### Post by dpar on 2007-06-08
Hi;
Got to terminal and post the output of ```
gedit /etc/apt/sources.list
```

---

### Post by Nythain on 2007-06-08
ok, lets try it this way... in terminal type
```

gksudo gedit /etc/apt/sources.list

```at the very top, or at least somewhere near the top, should be a line or two mentioning cdrom drive... im not sure exactly what it looks like since its been a while since i've seen it.

once you find those lines, either put a # in front of them (wich is called commenting it out, it makes things ignore that line, commonly used in programming so you could write a comment about the section of code, thus the term commenting out)

or just delete the line all together (i dont recomend this, just in case its the wrong line, would hate to have you delete an actual important repository entry)

once commented out... save the file then, in terminal type
```

sudo apt-get update

```and try to install again, this time it should look in the online repositories instead of the cdrom drive

hope that made a bit more sense

---

### Post by tahuya_rat on 2007-06-08
Seriously, dude, I'm running a full-on Ubuntu laptop,  and a dual-boot main box, do we really need to be so obtuse as not to answer in a way that a human being can understand?  I'm glad you got around to it, but this guy just needed a simple answer.

---

### Post by Gleep on 2007-06-09
> **Nythain said:**
> ok, lets try it this way... in terminal type
```

gksudo gedit /etc/apt/sources.list

```at the very top, or at least somewhere near the top, should be a line or two mentioning cdrom drive... im not sure exactly what it looks like since its been a while since i've seen it.

once you find those lines, either put a # in front of them (wich is called commenting it out, it makes things ignore that line, commonly used in programming so you could write a comment about the section of code, thus the term commenting out)

or just delete the line all together (i dont recomend this, just in case its the wrong line, would hate to have you delete an actual important repository entry)

once commented out... save the file then, in terminal type
```

sudo apt-get update

```and try to install again, this time it should look in the online repositories instead of the cdrom drive

hope that made a bit more senseThanks, that makes sense, I didn't want to wait very long for an answer, so I just stuck the alternate CD in and that worked fine but you actually made sense, so thanks.

I've now got KDE running and I just have the problem that screen res is a bit off, like for a start it's completely square, god knows who has a perfectly square screen for this to even be an option needed, but hey. I reckon once I work out how to change it all should be good. Till then, I'm using Gnome still.

I blame all my confusion on being a girl :-\":-\"

---

