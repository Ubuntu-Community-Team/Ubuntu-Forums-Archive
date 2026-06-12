---
title: "apt-get question"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by fuscia on 2005-11-28
when you use apt-get instead of synaptic, does it install the same dependencies? more? fewer?

---

### Post by fog on 2005-11-28
The same. Synaptic is a gui for apt-get.

---

### Post by ofek on 2005-11-28
Synaptic is apt-get frontend which means that synaptic is just a graphic way to execute the apt-get commands.

---

### Post by Brunellus on 2005-11-28
the same.  apt-get is just faster, especially if you know exactly what you need.

---

### Post by aysiu on 2005-11-28
Same.
There's a setting in Synaptic where you can choose to always have "recommended" packages be considered dependencies.

Maybe in apt-get there's an extra option for enabling this as well.

---

### Post by Kyral on 2005-11-28
[QUOTE=aysiu]Same.
There's a setting in Synaptic where you can choose to always have "recommended" packages be considered dependencies.

Maybe in apt-get there's an extra option for enabling this as well.[/QUOTE]
Apt-get doesn't

Aptitude DOES

```
sudo aptitude -r install <package>
```

---

### Post by Kyral on 2005-11-28
[QUOTE=aysiu]Same.
There's a setting in Synaptic where you can choose to always have "recommended" packages be considered dependencies.

Maybe in apt-get there's an extra option for enabling this as well.[/QUOTE]
Apt-get doesn't

Aptitude DOES

```
sudo aptitude -r install <package>
```

---

### Post by phoenix24x on 2007-09-19
so...ubuntu comes with 2 (prolly more) packages managers:

apt-get
aptitude

the GUI frontend to apt-get is synmaptic (sp), does aptitude also have a gui frontend?

---

### Post by Malibu Illusion on 2007-09-19
Aptitude itself is a front-end to APT.  It has a curses-based method of displaying its menus.

Type this to see it:

```
sudo aptitude
```

---

### Post by Maestro23 on 2007-09-19
apt-get vs. aptitude: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by fuscia on 2007-09-20
> **fuscia said:**
> when you use apt-get instead of synaptic, does it install the same dependencies? more? fewer?

newb!

---

