---
title: "cant install any applications"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Cpt Black on 2007-11-06
Hi,

I've just installed gutsy but can't seem to install any applications using either the add/remove in the applications menu or in the terminal. I tried entering the following command to get my fans to work properly
> sudo apt-get install i8kutils sensors-applet hddtemp
but got the following error:
> 
$ sudo apt-get install i8kutils sensors-applet hddtemp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package i8kutils

Cheers
CB

---

### Post by Dr Small on 2007-11-06
I do not know if any of those packages are in the universe repository or not, but you could try enabling the universe repository and see if that helps.

System > Administration > Software Sources
And find Universe and enable it.

Dr Small

---

### Post by markharding557 on 2007-11-06
it is definatly in the universe rep

---

### Post by Cpt Black on 2007-11-06
> **Dr Small said:**
> I do not know if any of those packages are in the universe repository or not, but you could try enabling the universe repository and see if that helps.

System > Administration > Software Sources
And find Universe and enable it.

Dr Small

That solved it cheers.

Interesting that none of the options were automatically ticked so I couldn't download any new package or program!

---

