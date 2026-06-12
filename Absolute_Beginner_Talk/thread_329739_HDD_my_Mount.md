---
title: "?HDD my Mount"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by jas992 on 2007-01-02
Hi!

I cannot locate my two HDD's. I installed Ubuntu yesterday as my sole OS. i.e. no Windows XP. I assume I must mount my drives but I cannot figure out how too. I have done some reviewing of relevant posts on this forum but cannot find a detailed explanation that I can follow. I am new to Linux but am enjoying the experience so far, even if I cannot access my HDD's!
Any information or directions would be greatly appreciated.

Yours truly,
Jas992

---

### Post by Malta paul on 2007-01-02
Hi welcome
Go to Applications>Accessories>Terminal and Type in 'sudo Fdisk -L' for list.

Hope this helps :)

---

### Post by bigken on 2007-01-02
its sudo fdisk -l

---

### Post by anaconda on 2007-01-02
Removable HD:s are regognised automatically, so I guess your HD:s are internal. If you would have had them connected when you installed ubuntu, they would have been found "automatically", but now you will have to add them to your /etc/fstab -file
Here are a few howtos:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

More general info:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by jas992 on 2007-01-02
I typed sudo fdisk -l into the terminal and a bunch of information on my drives was displayed. How can I access these drives in a similar fashion as I would through Windows Explorer in Windows XP? i.e. under 'Places' -> 'Computer' in Ubuntu. Should Ubuntu do this automatically on installation? Maybe I have done something wrong...

Furthermore, both my HDD's are internal and they were both connected on installation. If none were connected I would not have been able to install the Ubuntu OS.

---

### Post by indytim on 2007-01-02
You haven't done anything wrong.  Just follow the links Anaconda gave you and things will be good again in HD land.

IndyTim

---

### Post by Malta paul on 2007-01-02
The references that anaconda gave you should help you a lot'
If you still have a problem post the results of fdisk -l (thanks bigken!) you are doing fine so far :)

---

