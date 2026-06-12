---
title: "unbuntu"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by rhiel_jheanne on 2008-01-22
[COLOR="Blue"][SIZE="5"]I'm a newbie and I´m using Ubuntu Linux here is my problem...
 
     1. Everytime I type apt-get install -f...this will appear ...

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

     can you help me...
[/SIZE][/COLOR]

---

### Post by PriceChild on 2008-01-22
close "add remove programs" or "synaptic" or any other of those programs you have open.

---

### Post by MetalMusicAddict on 2008-01-22
Update-manager could also hang you up.

---

### Post by Nano Geek on 2008-01-22
Hello there,

First off, a couple of suggestions/comments:[LIST]
[*]Forum Feedback & Help is not the place to ask questions concerning Ubuntu. It is a place for people to make suggestions and ask questions about the forums only.
[*]It's slightly annoying when you write in big blue letters like that. If you don't mind, could you keep it to normal size and color?
[*]And finally, it's Ubuntu not unbuntu.[/LIST]Judging from that error message, it sounds like you have another program that installs programs such as Add/Remove... or the Update Manager running. 

Only one of those programs can run at a time and you need to close the others before you install something from the command-line.

EDIT: It looks like I was beaten to the punch. :)

---

### Post by dstew on 2008-01-22
> Everytime I type apt-get install -f...this will appear ...Try ```
sudo apt-get install -f...
```

---

