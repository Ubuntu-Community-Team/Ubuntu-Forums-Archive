---
title: "is there any way to ping all IP of a class C network with one command?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-02-09
Hi
Thank you for reading my post
Is it possible to ping an entire class C network with ping command?
I need to see which computers respond and I can see.
our Router allows broadcasting and ping command.



Thanks

---

### Post by dbutler on 2008-02-09
for N in `seq 1 254`; do ping -c 1 192.168.1.$N | grep ttl; done

---

### Post by amingv on 2008-02-09
Being a python apprentice, I saw this as the perfect occasion to try a small script (sacrilege, cries the Python purists):

[PHP]#!/usr/bin/python
#Filename: pingrange.py

from os import system as s

bulk = []

for i in range(1, 255):
    ip = '192.168.1.%i' %i
    if (s('ping -q -c 1 %s' %ip)) == 0:
        bulk.append(ip)

print 'Ip\'s listening:'
for item in bulk:
    print item
[/PHP]
Please, forgive...
[ATTACH]59202[/ATTACH]

---

