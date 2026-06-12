---
title: "Dual monitors"
date: 2007-02-20
forum: Apple PPC Users
---

### Post by wytygr on 2007-02-20
Hello all, I am running an Ibook G4 and I would like to use my external monitor also. I have tried multiple xorg configs and it just does not work. Before I put OS X back on the system, I figured I would give this forum a shot. Here is my video card:
 ATI Technologies Inc M11 NV [FireGL Mobility T2e] (rev 80)


thanks

---

### Post by beanworks on 2007-02-20
Which version of Ubuntu are you running?

Does Ubuntu see the monitor (for example, in the device manager)?

---

### Post by ssam on 2007-02-21
the ibooks video card can only mirror the main display on the external. you cannot make you desktop span two screen. (there maybe a firmware hack that makes it possible).

---

### Post by Kalvin on 2007-02-24
It may be worth trying the suggested changes to xorg.conf listed here: [http://www.ubuntuforums.org/showthread.php?p=1497267#post1497267]("http://www.ubuntuforums.org/showthread.php?p=1497267#post1497267")

Works for me...I have an iBookG4 with the Radeon 9000 chip as the author does but it should give you a good starting point.

---

### Post by oswaldkelso on 2007-02-25
> **wytygr said:**
> Hello all, I am running an Ibook G4 and I would like to use my external monitor also. I have tried multiple xorg configs and it just does not work. Before I put OS X back on the system, I figured I would give this forum a shot. Here is my video card:
 ATI Technologies Inc M11 NV [FireGL Mobility T2e] (rev 80)


thanks

There is a osx [hack ]("http://www.rutemoeller.com/mp/ibook/ibook_e.html") that work great but check your model first!!! I dont think its a hardware problem just apple trying to get people to buy powerbooks if the need extended desktops.

 as for ubuntu there is a howto[ here]("http://www.ubuntuforums.org/showthread.php?t=221174&highlight=dual+monitor").
On my debian box G4 digital audio Ihave a ati 9800pro card and run two old 21" monitors I suspect tyou have the apple mini external monitor cable? if so I would think it would be a similar setup but check the other howto first. 

heres my xorg file so you can see my setup.

---

