---
title: "automatix problem"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-09-17
I went ahead and tried automatix and it seemed pretty useful, but along the way while it was making the tweaks I told it to, it did say it couldn't install a few of them. this didn't worry me at first, but then when I cliked the software update button it said "It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first." I tried to do the terminal fix but it didn't work. What does this error mean and how do I fix it?

---

### Post by Najand on 2006-09-17
I think it is an automatix issue; use their forum to solve your problem.

---

### Post by catlett on 2006-09-18
> **mongooseman1128 said:**
> I went ahead and tried automatix and it seemed pretty useful, but along the way while it was making the tweaks I told it to, it did say it couldn't install a few of them. this didn't worry me at first, but then when I cliked the software update button it said "It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first." I tried to do the terminal fix but it didn't work. What does this error mean and how do I fix it?

What was the output of ```
sudo apt-get -f install
```
Did you try it with aptitude ? ```
sudo aptitude -f install
```
The issue sounds like an apt issue not an automatix issue. All automatix does is automate the normal apt package manger installation procedure. It isn't doing anything strange. It just enters all the commands for you. When you get that type of error it is usualy apt getting disconnected from the internet while downloading packages. The connection may have failed on your end or the server end but it is an apt issue that happened when automatix was using apt to install packages.
That is why you got > it did say it couldn't install a few of themThe connection failed and it couldn't install the applications. Anyways if your still havingh an issue, post the output from the command.

---

