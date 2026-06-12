---
title: "my dapper is freezing"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by bigodines on 2006-06-29
I'm runing dapper on a HP Compaq nx8220 and it was running smoothly for almost 1 month. (actually, since dapper was released hehe).

A couple days ago my system started to freeze withou any particular reason... First i was syncronizing my ipod using gtkpod and after the eject, the system stopped responding.

Yesterday it freezed two times when I was trying to read a dump from tcpdump. This morning it was when I was just editing a couple php webpages with eclipse.

I've saw on dmesg that there was something related to some interruption call from the hdb (cd/dvd). I tried to kill all process the were using this device and until now the system is ok (well.. uptime is 30 minutes, so this is not a parameter).

I'm writing this thread to see if anyone has had smilar problems and to ask sugestion on what can I do to try to find what this problem is.

Cheers,
Matheus

---

### Post by chadk on 2006-06-29
that topic subject makes me giggle. ;)

I'd check your RAM first.  Make sure your memory doesn't have issues.  This seems like either a memory problem or a heat problem (on your CPU).  Be sure the cooling fan for your CPU, graphics card and power supply are all CLEAN of any dust.

---

### Post by bigodines on 2006-06-29
ok, thanks for the quick reply. Would you mind to tell how to check these stuff? :P

btw: cooling is Ok.

---

### Post by digimars on 2006-06-29
checking memory is easy, just restart your computer and when Grub loads use the memtest option.  This will bring you into the RAM checker program.

---

### Post by bigodines on 2006-06-29
ok. thanks.

i'll do it and then I post the result

---

### Post by chadk on 2006-06-29
You could also put your dapper in a nice warm sock or some warm water (not too hot!) to warm it up then your dapper won't be freezing.  Sorry, couldn't resist.

---

