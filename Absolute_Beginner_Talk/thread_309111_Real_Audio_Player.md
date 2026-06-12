---
title: "Real Audio Player"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by bryan4134 on 2006-11-29
Could anyone recommend a good audio program that will play RAM (real audio files). I searched synaptic packages but could not find anything.  Sorry if this a stupid question....  Bryan

---

### Post by pay on 2006-11-29
First you need to add a repository
```
gksudo gedit /etc/apt/sources.list
```then add```
deb http://archive.canonical.com/ubuntu edgy-commercial main
```at the end of the file. Now install realplayer. ```
sudo aptitude install realplay
```

---

### Post by 3rdalbum on 2006-11-29
Missing step:

```
sudo apt-get update
```

Just before the last code block.

---

