---
title: "mplayer plugin mozilla"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by adza on 2007-03-12
I've been trying to install the mplayer plugin for mozilla from synaptic for a while now, it keeps pointing to unrecoverable dependancies.. does anyone know where i can get an install for this? Will this come back into the repositories soon?

---

### Post by xyz on 2007-03-12
Just to make sure you do have the repos:
First you need to add the following lines to /etc/apt/sources.list file

gedit /etc/apt/sources.list

enter these two lines and save your file

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
Then you can try running:
```
sudo aptitude install mozilla-mplayer
```

---

