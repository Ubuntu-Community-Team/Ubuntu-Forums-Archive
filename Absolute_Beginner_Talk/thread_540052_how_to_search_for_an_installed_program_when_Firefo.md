---
title: "how to search for an installed program when Firefox asks you which program you want."
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2007-09-01
Hi, 
This questionhas been asked before and I feel silly for not bookmarking it.
Also I searched the forum and could not find the threat again and quit frankly I dread searching for it in google. I apologize in advance for asking this.

you know when you download something from the net and firefox does not know which program it needs to open it and it asks you which program you want to use? How do I search for those programs? 
In M$ i know i need an .exe and those are in the program file, but in ubuntu i don't know where to look.

Can anybody help me with this (ridiculous simple) question (which i should allready know since I've been using Ubuntu for six months allready)...

---

### Post by sumguy231 on 2007-09-01
Most applications are in /usr/bin, but if you want to know where the executable for a command/program, type 'which <program>'. For example:
```
sumguy231@formalwear:~$ which firefox
/usr/bin/firefox
```

---

### Post by aitorcalero on 2007-09-01
Just type the name of the command you want to use. For exmaple, if you want to associate PNG files with gimp just type gimp, since gimp binary is in path it will automatically loads, no need to worry about paths anymore (linux point!) ;)

---

### Post by sumguy231 on 2007-09-01
Err, or that. I guess that makes a lot more sense, I didn't think of it since I use the alternate filepicker which doesn't have a location bar. So I completely forgot there was one in the default filepicker. Oops. Basically, disregard my first advice.

---

### Post by quinnten83 on 2007-09-07
well, 
pointing me to usr/bin was a good idea, as that works for what I need to do :)

Tnx both of you for your help.

---

### Post by hyper_ch on 2007-09-07
most program locatinos will be in the $PATH variable so you just need to type the name of the program and it will start...

e.g.

mozilla-firefox
kontact
...

---

