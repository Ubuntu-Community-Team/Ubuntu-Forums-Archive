---
title: "Automatix"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by vagery on 2006-11-09
I feel like a complete idiot, i cant install automatix, when i try to open source.list i cant save it...

does anyone know what im doing wrong?

---

### Post by LLRNR on 2006-11-09
Hi vagery, I think [this](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38) ought to help you out.

Good luck !

LLRNR

EDIT : If you use Dapper 6.06 (as you say you do), then look under the section labelled "Installing on (K,X)Ubuntu 6.06 i386,amd64 (Dapper)"

---

### Post by vagery on 2006-11-09
> **LLRNR said:**
> Hi vagery, I think [this](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38) ought to help you out.

Good luck !

LLRNR

EDIT : If you use Dapper 6.06 (as you say you do), then look under the section labelled "Installing on (K,X)Ubuntu 6.06 i386,amd64 (Dapper)"
i tried it, i think the problem is that im using a PPC prossesor

---

### Post by frodon on 2006-11-09
I advice you to post your question on the automatix forum thus you will get support from the developpers directly :
[http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/)

---

### Post by localuser on 2006-11-09
> **vagery said:**
> I feel like a complete idiot, i cant install automatix, when i try to open source.list i cant save it...

does anyone know what im doing wrong?

What command are you using to open source.list?

---

### Post by vagery on 2006-11-09
```
sudo gedit /etc/apt/sources.list 
```

that just gives me a blank file, if i try to open it manualy, and then save it, it says that i cant save...

Edit: now this is just me being a n00b,
i go through all of the steps and at the very end it hits me with ```
E: Couldn't find package automatix2
```

---

### Post by linkinPark on 2006-11-09
Check the case, i had a similar problem until i figured out that the terminal is case sensative.

---

### Post by navneeth on 2006-11-09
I installed Automatix just yesterday without any problem. 

Try this...
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by vagery on 2006-11-09
Ill check that out,

thnx for all the quick replys everyone...

---

### Post by vagery on 2006-11-09
> **navneeth said:**
> I installed Automatix just yesterday without any problem. 

Try this...
```
gksudo gedit /etc/apt/sources.list
```
OMG, i dont know what is was doing wrong, but it is now working...


EDIT: "I dont know what im doing now but i follow all of the steps and then it tells me that: ```
E: Couldn't find package automatix2
```

sorry bout the double post

---

### Post by navneeth on 2006-11-09
Glad to hear, but there is nothing wrong with the first code; in fact, I used only that. :)

---

### Post by arnieboy on 2006-11-09
just a heads up. we are not currently supporting ppc arch on automatix2 because of sheer lack of developers.

---

### Post by vagery on 2006-11-09
> **arnieboy said:**
> just a heads up. we are not currently supporting ppc arch on automatix2 because of sheer lack of developers.
are there any plans of coding automatix2 for ppc on edgy for the futre?

or, is there any way of downgrading from edgy to dapper?

edit: is there some sort of alternative for automatix?

---

### Post by localuser on 2006-11-09
> **vagery said:**
> is there some sort of alternative for automatix?

There's Easy Ubuntu that may be able to help...

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

