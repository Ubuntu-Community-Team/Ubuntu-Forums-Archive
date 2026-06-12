---
title: "need help installing programs"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by James2k6 on 2006-06-30
i download programs for ubuntu and dont understand install files i can run config but not make if any body could help me through it that would be great.  programs such as lime wire or another p2p and zsnes (a snes emulater)

---

### Post by chajuram on 2006-06-30
Hi,

There are a number of ways you can install programs, if you are talking about installing a program from the source code, then you will have to configure make etc (usually the README file has the instructions). However, many programs are already kept in formats which can be installed with one click or a one line command, for a good set of instruction see

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

In addition you can also use synaptic package manager for a gui way of installing packages. 
You can also use [automatix]("http://www.ubuntuforums.org/showthread.php?t=138405") to install Frostwire a clone of limewire.
 
Chajuram.

---

### Post by invalid on 2006-06-30
[QUOTE=James2k6]i download programs for ubuntu and dont understand install files i can run config but not make if any body could help me through it that would be great.  programs such as lime wire or another p2p and zsnes (a snes emulater)[/QUOTE]
Sounds like you do not have the programs to compile and make the source.
```
sudo apt-get install build-essential
```

---

### Post by joshrobinson on 2006-06-30
[QUOTE=invalid]Sounds like you do not have the programs to compile and make the source.
```
sudo apt-get install build-essential
```[/QUOTE]

yeah you  need build-essential.. then make might tell you that other things need to be installed also, and you can grab them from synaptic or an apt-get command
last time i did zsnes it required a few other things to get past the make stage

also for p2p/limewire use frostwire, its almost the same exact thing, but comes ready to use in repo's and on their website

---

### Post by Jagot on 2006-06-30
You can find out more about installing here:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)

---

