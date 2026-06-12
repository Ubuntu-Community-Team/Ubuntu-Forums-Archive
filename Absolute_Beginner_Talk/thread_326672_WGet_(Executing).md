---
title: "WGet (Executing?)"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Straft on 2006-12-28
I'm very new to Ubuntu and Linux, and all the other distro's. I downloaded WGet 1.9 and it's just a package with files...

[IMG]http://img223.imageshack.us/img223/1821/screenshotsi8.png[/IMG]

Ok, so since I'm so used to Windows it has warped me to think theres aways going to be an executable. Well what do I execute to make this program run? OR do I execute anything? Basicly what I'm wondering is, how do I run the program?

-Straft

---

### Post by dbbolton on 2006-12-28
in a terminal:
```
 wget 'url'
```

where 'url' is the location of a file you want.

---

### Post by dbbolton on 2006-12-28
wait, did you install the wget packages from synaptic package manager ?

that would be the way to go.

---

### Post by Straft on 2006-12-28
> **dbbolton said:**
> in a terminal:
```
 wget 'url'
```

where 'url' is the location of a file you want.

Thank you, this will help me very much in the future :)

---

### Post by Straft on 2006-12-28
> **dbbolton said:**
> wait, did you install the wget packages from synaptic package manager ?

that would be the way to go.

Uhm...no? I don't think so, just saved the file onto my desktop and extracted the folder onto my desktop.

---

### Post by po0f on 2006-12-28
Straft,

dbbolton is talking about [this](http://packages.ubuntu.com/edgy/web/wget), wget is in the repos, no need to download it yourself.

---

### Post by pistcivet on 2006-12-28
GWGET is a gui front end for wget, its also in the repos.

There is a nice Firefox extension for integrating Gwget, called "Fireget"
If you're interested, you can find it here:
[http://www.gnome.org/projects/gwget/](http://www.gnome.org/projects/gwget/)

---

### Post by kerry_s on 2006-12-28
Wget is always installed on every linux system by default, there's no need to install it.

---

