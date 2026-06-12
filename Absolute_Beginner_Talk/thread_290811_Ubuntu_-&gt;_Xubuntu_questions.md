---
title: "Ubuntu -&gt; Xubuntu questions"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by eilu on 2006-11-01
Currently running Ubuntu 6.10 (dapper); originally becuase I just wanted to try it out but now I'm using it more than Win98 (and considering throwing Windows out)

My system is a PIII 600Mhz with 256MB ram (used to be more, but one stick died and I haven't replaced it yet) so I'm thinking it might be better to run Xubuntu, but I have a few questions:

[LIST=1]
[*]Should I get 6.06 or 6.10? It doesn't have to be the "latest and greatest," it just has to work.

[*]Is OOo included in Xubuntu by default? I looked online and I'm not sure, some sites said "Xubuntu (only) has Abiword and Gnumeric" others said it had/also had OOo :confused: Really need OOo for uni, so if this isn't on it might be a no-go for now.

[*]Will Frozen Bubble run on Xubuntu? Okay, this isn't important, but that game is addicting! :mrgreen:
[/LIST]

---

### Post by Kateikyoushi on 2006-11-01
Dapper is version 6.06 and edgy eft is 6.1
You do not have to do a complete new install to use xfce.
The following line should do and you can still use OOo the best of both worlds.

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

---

### Post by psycosmyth on 2006-11-01
I use 6.06, it is easier on the old processor, I have Gnome too. Ooo is not included with Xfce 6.06 but is easily added. I have'nt tried 6.10 or Frozen bubble. Xfce lacks all the crap so it is faster though.

---

### Post by Bartender on 2006-11-01
Looks like it's [there]("http://www.mail-archive.com/xubuntu-devel@lists.ubuntu.com/msg01964.html") but maybe not in the default install.

---

### Post by jpeddicord on 2006-11-01
I highly reccommend version 6.06 (Dapper Drake) because it is very stable and supported long term.

And yes, Frozen Bubble does work on it, although it is not the latest version.

Jacob

---

### Post by eilu on 2006-11-02
> **Kateikyoushi said:**
> Dapper is version 6.06 and edgy eft is 6.1
You do not have to do a complete new install to use xfce.
The following line should do and you can still use OOo the best of both worlds.

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

I tried this, but I'm on dial-up... 2 hours and not even 10% done, so I gave up; I've been told the alternative install CD can do something similar though, so I'll try that one.

And thanks for everyone's replies. Xubuntu 6.06 it is then...

---

### Post by mahy on 2006-11-02
According to Distrowatch, Xfce in Dapper is of higher version number than in Edgy. ;)

---

### Post by gn2 on 2006-11-02
> **eilu said:**
> I tried this, but I'm on dial-up... 2 hours and not even 10% done, so I gave up; I've been told the alternative install CD can do something similar though, so I'll try that one.

And thanks for everyone's replies. Xubuntu 6.06 it is then...

If you have an Ubuntu install CD, you could install Ubuntu then add xubuntu-desktop through Synaptic.

I did this recently and it's a 46mb download. Don't remember how long that would take on dial-up, I consider myself very fortunate to have the facility of 2meg ADSL. You have my sympathies, I used to hate dial-up.

Xubuntu is a bit faster than Ubuntu, but it won't transform your PC into a rocket-ship speedwise.

---

