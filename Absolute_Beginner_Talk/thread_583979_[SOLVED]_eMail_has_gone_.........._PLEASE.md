---
title: "[SOLVED] eMail has gone .......... PLEASE"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by tahitiwibble on 2007-10-20
The online upgrade from 7.04 to 7.10 has just finished and I can no longer find any of my Thunderbird files or even the program ................ I am sweating buckets of cold sweat!!!!!!!!!! and my stomach is somewhere in space:confused::confused::confused::confused::confused:

---

### Post by Sef on 2007-10-20
Check System > Preferences > Main Menu > Internet.

---

### Post by Frak on 2007-10-20
Type
```
thunderbird
```
In the terminal (Applications->Accessories->Terminal).
If it appears, goto System -> Preferences -> Main Menu -> Internet and check Thunderbird.

If it doesn't appear, click the link below and answer "yes"
[apt:thunderbird]("apt:thunderbird")

---

### Post by psycosmyth on 2007-10-20
you can also try the Lost&found dir as root. I have seen info like saved passwords ans user settings end up there.

---

### Post by tahitiwibble on 2007-10-20
SEF, thank you Sir, just your presence allowed me to come out of that state of total panic and the problem is resolved.

For some reason the links to the program were removed. Now I'm going to find out where the files are located for a new backup strategy

---

### Post by tahitiwibble on 2007-10-20
**THANK YOU** Gentlemen ............... most sincerely! Every little bit helps.

---

### Post by bruce89 on 2007-10-20
```
sudo aptitude reinstall mozilla-thunderbird
```

---

