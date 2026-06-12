---
title: "software source"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by catch2two on 2007-07-25
Please help it seems like everything i try and fix ends up being ten new problems. I just wanted to play DVD. now my Software sources springs an error the synaptic package manager no longer works and i cant update my system.

I just want to go back to when it worked fine.

The error i get when i open either software sources or synaptic package manager are:

E: Type '¨deb' is not known on line 51 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

then when i x out it closes

---

### Post by lsutiger on 2007-07-25
Could you post your /etc/apt/sources.list file?

---

### Post by catch2two on 2007-07-25
It says denied

---

### Post by wolfen69 on 2007-07-25
this [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)   will make a new sources list for you. just delete the old one and replace.

---

### Post by catch2two on 2007-07-25
how do i do that i have the list it created i just dont know what to do with it

---

### Post by wolfen69 on 2007-07-25
in terminal:
```
gksudo nautilus
```
then navigate to /etc directory
then to apt directory
you will find sources.list there.
delete and replace.

---

### Post by catch2two on 2007-07-25
Thanks. 

You da man.

My blood pressure is returning to normal.

You dont happen to know how to get dvd&#347; to play without destroying my comp do youo?

---

### Post by wolfen69 on 2007-07-26
open synaptic and search for- libdvdcss2, and libdvdnav4.

---

### Post by lsutiger on 2007-07-26
You may have to add the medibuntu repository.
[Follow these instructions]("http://ubuntu1501.blogspot.com/2007/06/medibuntu-how-to-install-dvd-codecs.html").
They are straight forward and will not 'destroying your computer'

---

### Post by vexorian on 2007-07-26
I really think howtos that involve modiffying the repositories should begone or at least warn about how careful you got to be not to make a mistake when editing the sources list...

---

### Post by wolfen69 on 2007-07-26
you should be careful when doing anything, but fixing the sources list is relatively easy. that's why we're here on the forums!

---

