---
title: "How Do I Access Files As Root?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by liamwithers on 2007-10-19
Hi, I was just wondering, how do I access the Sources.list file as root so I can edit it?

Thanks, Liam

---

### Post by kevin11951 on 2007-10-19
push alt+f2 and:
"gksu gedit <path to file>"
or terminal
"sudo gedit <path to file"

---

### Post by skotadi on 2007-10-19
Maybe this is not as secure, but I usually just do 
alt+f2
and enter
```
gksudo nautilus
```

That way I can browse files and stuff as root

---

### Post by Paul820 on 2007-10-19
Terminal:
> sudo gedit /etc/apt/sources.list

---

### Post by xc3RnbFO8P on 2007-10-19
You can use Pcman File Manager

tool> open current folder as root

Pcman File Manager is in Add and Remove/ All available applications.

---

### Post by bodhi.zazen on 2007-10-19
'lo all

Please consider gksu (kdesu for kde) for graphical apps (gedit, nautilus, etc) :

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by aysiu on 2007-10-19
If you're using Ubuntu 7.10, I think you can just navigate to the /etc/apt directory and double-click on the sources.list file, which will then open up Software Sources.

Or, you can go to System > Administration > Software Sources directly.

---

### Post by Technoviking on 2007-10-19
Try installing nautilus-gksu
```
sudo aptitude install nautilus-gksu
```

---

