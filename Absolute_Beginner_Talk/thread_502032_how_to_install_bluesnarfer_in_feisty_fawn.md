---
title: "how to install bluesnarfer in feisty fawn??"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by malanco on 2007-07-16
hi , im a ubuntu feisty fawn user, im new here in linux, my question is : how can i install bluesnarf in ubuntu, i didnt find any repo to install with apt-get , i need some help here.

thanks :)

---

### Post by malanco on 2007-07-16
plz help! anyone??

---

### Post by YaronSh on 2007-08-16
I believe it would be unethical but since i'm not the most ethical guy in the world i should tell you that you should compile it from source...

---

### Post by pana.corbului on 2007-11-08
so make doesn't work; how do i install bluesnarf from source? :D

---

### Post by skymera on 2007-11-08
personally i heard that Bluesnarfing is hacking bluetooth devices :confused:

although i may be wrong.

to compile you must first download the tar.gz

---

### Post by pana.corbului on 2007-11-08
> **skymera said:**
> personally i heard that Bluesnarfing is hacking bluetooth devices :confused:

although i may be wrong.

to compile you must first download the tar.gz

I've downloaded tar.gz ..I'm not that noob ... It's not like ./configure, make && make install ...it;s compile  from c source file...uses gcc I assume

---

### Post by ChunkyBAllz on 2007-12-11
Can anyone tell me how to download a bluesnarf programme or a link to one. plz i have been looking for weeks.

---

### Post by skroops on 2007-12-11
if you've been looking for weeks you could just see that its linked to on the wikipedia article on bluesnarfing

---

### Post by ChunkyBAllz on 2007-12-14
Can u just leave me a link please???

---

### Post by pana.corbului on 2007-12-24
You can install bluesnarfer this way: 
sudo aptitude install libbluetooth2-dev

download bluesnarfer.tar.gz, uncompress, navigate to directory, and use this command:

```
gcc -Iinclude -W -g3 -lbluetooth src/bluesnarfer.c -o bluesnarfer
```

---

### Post by Fatjoint on 2007-12-24
Cracking is illegal, when you're attempting to crack a system that you don't have permission to access.

The OP in this case is wishing to load a program that could potentially be used for cracking, but using a utility is not the same as using a utility in an illegal manner.  The programs ping, arp, and nmap, can be used in an illegal manner, but are crucial to understanding and diagnosing network issues - curiosity is what brought me to Linux in the first place.

I've been a member of Ubuntu Forums for a few years now and would really be disappointed if we evolved into a group that made it our business in how a person is going to use a program, and based that decision on whether or not we helped someone.

---

### Post by pana.corbului on 2007-12-25
What I don't see is why do people always presume that one can use bluesbarf to crak someone's phone..I just don't get it. It's his prolem not yours . I think it's a matter of perspective. Why can't you assume that maybe all he wants is  to experiment on his own phone just to see if it works. This example would apply also to wep craking or nmap, ettercap, airsnort, kismet, etc etc.

---

### Post by boast on 2008-05-28
yes, old, but just incase anyone else needs to know


apt-get install libbluetooth-dev   

first

---

