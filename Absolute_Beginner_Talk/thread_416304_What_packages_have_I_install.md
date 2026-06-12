---
title: "What packages have I install?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-04-21
Is there a list of all the packages I have installed via aptitude anywhere? some sort of log?

---

### Post by heimo on 2007-04-21
```
dpkg --get-selections
```

or

```
aptitude search "~i"
```

---

### Post by jtraub on 2007-04-21
/var/log/aptitude

---

### Post by jtraub on 2007-04-21
Synaptic logs are located in /root/.synaptic/log directory

---

### Post by guysmiley25 on 2007-04-21
I do not think that theses are what I after. I remember a while ago there was some log of some kind that listed all my actions installing and uninstalling packages.

---

### Post by heimo on 2007-04-21
> **guysmiley25 said:**
> I do not think that theses are what I after. I remember a while ago there was some log of some kind that listed all my actions installing and uninstalling packages.

Try System->Administration->Synaptic Package Manager->File->History.

---

### Post by guysmiley25 on 2007-04-21
Not there. I suspect this is because I use aptitude/apt-get. However I sure there is a log file that exist but I cant find it.

---

### Post by heimo on 2007-04-21
> **guysmiley25 said:**
> Not there. I suspect this is because I use aptitude/apt-get. However I sure there is a log file that exist but I cant find it.


```
less /var/log/dpkg.log
```

---

### Post by guysmiley25 on 2007-04-21
Chears that will work, however from my memory there was a differnet log. Maybe it&#347; because Ive upgraded.

---

### Post by heimo on 2007-04-21
> **guysmiley25 said:**
> Chears that will work, however from my memory there was a differnet log. Maybe it&#347; because Ive upgraded.

Maybe it has been rotated. Old logs are moved to archives. For a log file like messages, it's first moved to messages.0, then when it's rotated again, it'll become messages.1.gz, messages.2.gz and so on, until it gets removed (depends on settings). Check your older logs. zless / zgrep and the like are nice shortcut for handling those compressed ones.

---

