---
title: "install .tar.bz2"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-08-13
Um. I'm not the most familiar with installing this. I have extracted it. Went through the terminal. did sudo apt-get build-essential. did cd in the terminal to get to the right directory (where I extracted) and did ./configure. But ./configure doesn't work. Help please.

---

### Post by bodhi.zazen on 2007-08-13
.tar.bz2 

is an archive, like a zip file. It can contain source code, python scripts, or executable binaries.

you need to read the README

Or, what are you trying to install ?

---

### Post by CapitanYochua on 2007-08-13
I read that I should type in "make" into the terminal. then check install. So I am trying that. 
And there was no README.

---

### Post by CapitanYochua on 2007-08-13
It's a game called Open Arena. Help please...
I have noticed a makefile. If that says anything.

---

### Post by bodhi.zazen on 2007-08-13
if there is a make file, skip ./.configure

```
make
sudo make install
```

---

### Post by blithen on 2007-08-13
getdeb.net
Search for it there, download all 3 things, and then just double click and run all three. then one with DATA in it first.
Then from there the other two can be done in whichever order.

---

### Post by CapitanYochua on 2007-08-13
> **bodhi.zazen said:**
> if there is a make file, skip ./.configure

```
make
sudo make install
```
this was my output from that command.
make: *** No rule to make target `install'.  Stop.



Couldn't find it on that site.

---

### Post by darksidedude on 2007-08-13
open arena is in the add/remove AKA synaptic

it is also at  [http://www.getdeb.net/app.php?name=OpenArena](http://www.getdeb.net/app.php?name=OpenArena)

---

### Post by CapitanYochua on 2007-08-13
wow. I feel dumb. thanks though! Which do I choose? the 32 bits or the 64?

---

### Post by CapitanYochua on 2007-08-13
which do I pick?

---

### Post by amazingtaters on 2007-08-13
do you have a 32 bit or 64 bit processor

---

### Post by CapitanYochua on 2007-08-13
Not sure. Where/how can I check?

---

### Post by bodhi.zazen on 2007-08-14
gui : System -> Preferances -> Hardware Information

cli : (terminal) cat /proc/cpuinfo

---

