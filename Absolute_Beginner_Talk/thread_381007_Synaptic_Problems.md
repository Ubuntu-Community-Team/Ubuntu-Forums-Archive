---
title: "Synaptic Problems"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by gameman12 on 2007-03-10
hi all,

i am trying to install network manager with synaptic package manager and it is not there. i also  can't download anything new for the manager because i can't get on the interenet.

one more thing, i also tried apt-get installing network manager from a terminal and i get

E: ccouldn't find package

---

### Post by bulldog on 2007-03-10
Well if you have no internet access on your computer,you can't download anything with apt-get or synaptic.
You'll have to make your connection to work before you can use the programs.

You can however enable the install cd as a source in your sources.list.

[# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Alpha i386 (20070215.2)]/ feisty main restricted]
Remove the # from the beginning of the line and pop in the cd-rom.

You'll find your sources.list with```
gksudo gedit /etc/apt/sources.list
```

---

### Post by gameman12 on 2007-03-11
thx bulldog, i just tried that but it still doesn't show in synaptic. what else could be the problem??

---

