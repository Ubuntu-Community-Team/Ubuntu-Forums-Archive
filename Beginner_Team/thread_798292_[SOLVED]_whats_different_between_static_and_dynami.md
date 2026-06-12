---
title: "[SOLVED] whats different between static and dynamic opera ??"
date: 2008-05-18
forum: Beginner Team
---

### Post by neo_adi on 2008-05-18
well i tried to install opera browser into my ubuntu.. 
i was struck by this thing .. 

there were two setups one with static and the other with dynamic. 
can anybody here help me know what it is and what its all about ?? 


ps: dont mind if its too silly question :(

---

### Post by hessiess on 2008-05-18
static, everything is compiled into the binery.
dynamic, the binary links to external libarys.

---

### Post by neo_adi on 2008-05-18
> **hessiess said:**
> static, everything is compiled into the binery.
dynamic, the binary links to external libarys.

can you be more precise please... :???:
well is it with the library files with which the development of opera are associated ?? 


ps: never mind if its too silly

---

### Post by dreadlord_chris on 2008-05-18
> **neo_adi said:**
> can you be more precise please... :???:
well is it with the library files with which the development of opera are associated ?? 


ps: never mind if its too silly

Static (in this context) basically means that **all** the code to run the app is included. As a consequence they tend to be bigger.

Dynamic, on the other hand, assumes that some (the dynamically linked libs) code is already installed on the target system.

Basically, what it comes down to is this - *statically linked* apps are more _distro_ independant, and therefore tend to be more generic. Whereas, *dynamically linked* apps will usually integrate with a system (especially the look-n-feel) much better.

and just so you know - you're probably better off with the dynamically linked Opera...

---

### Post by sdennie on 2008-05-19
The above post is correct.  However, I don't recommend downloading opera from the website (unless for some reason you are in dire need of the latest version).  Go to System->Administration->Software Sources->Third-Party Software and select the two options (that should be) there.  Then, in a terminal, type:

```

sudo apt-get update
sudo apt-get install opera

```

That will properly install opera on your machine without having to deal with the hassle of installing something manually.

---

### Post by neo_adi on 2008-05-19
well thanks for the reply.. 

@vor: well the very intention was to install an application manually :D

---

### Post by LaRoza on 2008-05-19
> **vor said:**
> The above post is correct.  However, I don't recommend downloading opera from the website (unless for some reason you are in dire need of the latest version).  Go to System->Administration->Software Sources->Third-Party Software and select the two options (that should be) there.  Then, in a terminal, type:

```

sudo apt-get update
sudo apt-get install opera

```

That will properly install opera on your machine without having to deal with the hassle of installing something manually.

I always get it from the site. Right now, I use Opera 9.50b2. 

You get a .deb file and you double click it (give password). Then, it finds the two dependencies (if you don't already have them) and installs them from the repos. Then it unpacks ands installs. You don't have to do anything. It is painless and easy.

---

