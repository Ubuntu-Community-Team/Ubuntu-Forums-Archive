---
title: "How do you download things off trevino's repository?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2007-09-26
Hi, I don't know how to download compiz plug-ins and such off trevino's repository. (I just got 7.10 so the unsupported plug-ins (and others) doesn't appear in synaptic). I was just wondering since everythings still very new to me.:KS

---

### Post by mesilliac on 2007-09-26
As far as I know, trevino's repositories don't support gutsy (ubuntu 7.10). Sorry :).

---

### Post by Billy_McBong on 2007-09-26
[COLOR="Blue"]gusty is still in beta so i don't know if this will work but in feisty you open your source list
```
sudo gedit /etc/apt/sources.list
```
and add
```
# Treviño’s Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, compiz and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs…

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

# Treviño’s Ubuntu feisty EyeCandy Repository end
```

here is his guide for how to install it
[http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/]("http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/")
[/COLOR]

---

### Post by nikoPSK on 2007-09-26
Thanks. I'm thinking of switching back to feisty until the 18th:KS

---

### Post by ThrobbingBrain66 on 2007-09-26
> **Billy_McBong said:**
> [COLOR="Blue"]gusty is still in beta so i don't know if this will work but in feisty you open your source list
```
sudo gedit /etc/apt/sources.list
```
and add
```
# Treviño’s Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, compiz and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs…

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

# Treviño’s Ubuntu feisty EyeCandy Repository end
```

here is his guide for how to install it
[http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/]("http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/")
[/COLOR]

It will work, but it's bad practice.  You can introduce bugs and create other problems by using repos that aren't compiled for the version/distro being used.

---

### Post by nikoPSK on 2007-09-26
I think I'll wait until the 7.10 official is out:popcorn: (toooooo loooooong)

---

