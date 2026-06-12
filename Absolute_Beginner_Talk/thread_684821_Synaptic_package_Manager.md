---
title: "Synaptic package Manager"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by appleimac on 2008-02-01
Is the Synaptic package Manager just the gui for 

```
apt-get install packagename
```

---

### Post by dannyboy79 on 2008-02-01
yes. but aptitude is better frmo the command line because when you install stuff using aptitude and it installs a bunch of other dependences they will also get removed when using aptitude remove packagename whereas apt-get just leaves them behind. also, aptitude can show what package is installed. example: sudo aptitude show ssh. it can also search all repo's for a certain package or name. example: sudo aptitude search nvidia. so although synaptic is nice, I prefer command line and aptitude.

here's a good explaination: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by appleimac on 2008-02-01
Thanks for the info about aptitude I did not no that :-)

---

### Post by SunnyRabbiera on 2008-02-01
both synaptic and aptitude are great for package installation.
Aptitude is no doubt the easiest command line based installer I have ever used as it dances the boarder between a gui and cli.
Its simple enough for beginners though I still direct people who are afraid of the terminal to synaptic.

---

### Post by appleimac on 2008-02-01
I try to do most things in the terminal its just quicker to type out a line of text than to go search through windows :-)

---

### Post by jan quark on 2008-02-01
I have heard somewhere that it is not recommend to mix the two installation types

I mean one package I install with apt-get 
the next one with aptitude
the next one with apt-get
and so on, you get the point

can this do some harm 
I just asking don't wanna spread a false information

---

### Post by SunnyRabbiera on 2008-02-01
> **appleimac said:**
> I try to do most things in the terminal its just quicker to type out a line of text than to go search through windows :-)

well if you were a total beginner though I would not have suggested a cli app unless it was needed on a personal level

---

