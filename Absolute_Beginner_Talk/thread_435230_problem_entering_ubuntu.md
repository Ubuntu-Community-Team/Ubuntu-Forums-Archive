---
title: "problem entering ubuntu"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-05-06
The problem is that after I enter my username and password the screen freezes and the welcome sound does not appear and after waiting a while a gray screen appears in the left side, but only a gray square I can't do anything and when I put the cursor over the square it changes as if it was a square where you can write or something like that...
So I pressed Ctrl+Alt+F1 and something like this appeared:
```

starting up...
[    16.405802]  ..MP-BIOS bug:8254 Timer not connected to IO-APIC

Loadin please wait...
kinit: name_to_dev_t(/dev/sda4) = Sda4(8,4)
kinit: trying to resume from /dev/sda4
kinit: No resume image, doing normal boot

Ubuntu 7.04 ubuntu tty1

Ubuntu login:

```
I tried with 
```

sudo /etc/init.d/gdm restart 
```
and nothing happened, still the same problem again.
The problem is that since the beginning of the installation this 
```

[    16.405802]  ..MP-BIOS bug:8254 Timer not connected to IO-APIC
```
appeared and still I had no problem.
Any ideas of what can be affecting me? any change from this guide can affect something?
[https://help.ubuntu.com/community/Wi...cs%2FDevice%29](https://help.ubuntu.com/community/Wi...cs%2FDevice%29)


Any ideas of how to fix it?

---

### Post by Happy_Man on 2007-05-06
It seems your BIOS is having a temper tantrum. What version is it?

---

### Post by Jorge32 on 2007-05-06
the problem of entering ubutnu is because of that? I have the F.06!

---

### Post by Jorge32 on 2007-05-06
Anbd besides I had no problem before even having that message.... and my comptuer stayed all day on withouth temperature problems, it even stayed cooler than in Windows!

---

### Post by Jorge32 on 2007-05-06
Some people say it is because of some hyperthreading in the Bios
 Cristian Aravena Romero said on 2007-04-30: (permalink) 

Problem with "Intel® Desktop Board D102GGC2"
* I update BIOS to Ver. 1087 date: 1/30/2007
* Install Ubuntu Feisty
* Reboot and not start Ubuntu

Solution:
* Press F2 and change in configuration of BIOS HyperThreading off (Work with 1 CPU)
 Cristian Aravena Romero said on 2007-04-30: (permalink) 

> It's a harmless message, the kernel detected the problem and worked around it.

NOT!!! Ubuntu not start in _install_!!! (Live CD Work with message of bug) test in:
* Ubuntu Dapper 6.06.1
* Ubuntu Edgy 6.10
* Ubuntu Feisty 7.4
* gNewSense 1.1

Problem is *default* enable HyperTreading in BIOS
 Cristian Aravena Romero said on 2007-04-30: (permalink) 

Problem *NOT* start Ubuntu in install. *FREEZE*, change in BIOS of enable to disable Hyper Treading and start


that is from, this page [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91279](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91279)


but how can I make that of disable the hypertreading on Bios, F2 and ctrl+alt+f2 didn't worked out....?????

---

### Post by Jorge32 on 2007-05-06
sorry to be writing too many times here....


I just found the F2 key is the one for the bios config in dell computers and mine is a HP Compaq nx6325, besides my bios config doesn't have anything like Hyper Treading....
 The question is why this just happened after reconfiguring the network card? is it because ndiswrapper is loading automatically or best said always? Network is working but now Ubuntu isn't.... and I can't find a solution... I tried several things and it just freezes at the begining...
please somebody help me that I am getting crazy!!!! haha
Any ideas ?

---

