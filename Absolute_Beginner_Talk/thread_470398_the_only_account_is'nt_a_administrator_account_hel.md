---
title: "the only account is'nt a administrator account? helpp"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by mark. on 2007-06-10
ok i feel bad for making continuous threads for help, 
but i just noticed most of the things i need to do are from this.


when i installed from live cd, the account 'mark' was what i used to register. but when i need to access things such as users/groups i cannot, because i am 'not allowed to access the system configuration'.

also, when i start my computer i get a 'cannot initialize HAL' message. and when i access certain things it asks me to enable 'hald' (which i think hal and hald are closely related)

can you help a linux noob? thanks in advance.

---

### Post by trent dillman on 2007-06-10
...

---

### Post by mark. on 2007-06-11
umm i did that and it said 'mark' was already added but when i rebooted i had the same problems :/

---

### Post by zvacet on 2007-06-12
Simply add** sudo** in front of command and that will give you admin rights.

---

### Post by mark. on 2007-06-12
oo thats shat sudo means lol. But i still have a problem opening administrative programs/managers because i cannot use a terminal command to open them, and for some reason am 'not allowed' to.

is there any way to dix the HAL error that pops up when i start my computer? i found a tutorial but it's outdated for dapper and wont work on my computer. 

thanks in advance :D

---

### Post by mark. on 2007-06-18
help anyone? i cant access any usb media =[

---

### Post by schorsch on 2007-06-18
I will use synaptic as an example:

GNOME:
```
gksu synaptic
```

KDE:
```
kdesu synaptic
``` ... ifI remember it right .... I don't use kde

This will start "synaptic" in graphical mode after you typed your password in administrative mode.

---

### Post by mark. on 2007-06-26
hmm, ok thanks--

what is the name to run for launching 
-removable drives and media
-services
-users and groups
(is there a link?)

thanks in advance, all :D

---

