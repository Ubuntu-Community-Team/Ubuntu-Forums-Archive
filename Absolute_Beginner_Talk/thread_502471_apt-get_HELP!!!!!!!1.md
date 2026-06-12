---
title: "apt-get HELP!!!!!!!1"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by p3ngu1n on 2007-07-16
ok, so i try to get new things through apt-get. but EVERY time i try to get something like, oh, say, sudo apt-get install gkrellm or sudo apt-get install supertux-stable, it says it cant find the package. i already tryed apt-get update but it didnt work. one time it told me to turn on "universal" or something so how do i get that on?

---

### Post by robertc36 on 2007-07-16
to install that way try searching

> sudo apt-cache search

---

### Post by wolfen69 on 2007-07-16
System-->Administration-->Software Sources    make sure all repos are checked

---

### Post by CautionaryX on 2007-07-16
You'll probably have to enable the universe and multiverse repositories to get the programs you want.

Open Synaptic then go to Settings > Repositories and make sure the universe and multiverse repositories are enabled.

---

### Post by p3ngu1n on 2007-07-16
wow. it worked! thanks :]

---

