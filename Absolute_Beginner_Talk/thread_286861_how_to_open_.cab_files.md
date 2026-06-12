---
title: "how to open .cab files?"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Xphome on 2006-10-28
How to open .cab files?

---

### Post by GStubbs43 on 2006-10-28
.cab files are Windows files, not Linux. It might work through WINE (I really don't know.) You *can extract* the .cab files with cabextract, but I'm not sure if that will help you. 
P.S. Please describe your problem better in your post rather than repeating your thread *title.* Thanks!

---

### Post by earnur on 2007-12-23
Hi, I've got same problem. I want extract .cab files. When I use cabextract
> eugeniusz@ubuntu:~/maciej$ cabextract /home/eugeniusz/maciej/data1.cab


and I get that reply

> 
/home/eugeniusz/maciej/data1.cab: WARNING; found InstallShield header. This is probably an InstallShield file. Use UNSHIELD ([http://synce.sf.net](http://synce.sf.net)) to unpack it.

/home/eugeniusz/maciej/data1.cab: no valid cabinets found


So, I installed unshield and type

> unshield -d /home/eugeniusz/maciej/data1/ x data2.cab

and reply was

> Failed to open data2.cab as an InstallShield Cabinet File

can someone help me with this, please?

---

### Post by Breakthrough on 2008-02-12
> **earnur said:**
> Hi, I've got same problem. I want extract .cab files. When I use cabextract


and I get that reply



So, I installed unshield and type



and reply was



can someone help me with this, please?

I'm having the same problem :(.
Could someone help?

---

### Post by PeterK. on 2008-03-03
> sudo apt-cache search cabextract

:idea:

---

### Post by TyTiger on 2008-06-06
Apparently Winzip opens .cab files, I've come across this issue myself... If you have Wine installed you should be able to use something like Winzip by just installing to wine then running it through that...

But I don't think Winzip is open source and bugs you to register or buy the full version so there's an option if your desperate

---

