---
title: "[SOLVED] cabextraxt not being found"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by funkshun on 2007-07-22
Can someone help me out with a link for cabextract for 6.06.1. I have gone to two sites and neither works. The file that I did download. Add/Remove programs could not find the file wich I downloaded to the desktop.I tried to do it throught the terminal and it gives me this:

funkshun@funkshun-laptop:~/ndiswrapper-1.47$ sudo apt-get install cabextract unzip
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package cabextract
funkshun@funkshun-laptop:~/ndiswrapper-1.47$

thanks

---

### Post by wolfen69 on 2007-07-22
sounds like you need to enable/add some repositories.

---

### Post by wolfen69 on 2007-07-22
it's(cabextract) in synaptic for me. go to system>admin.>software sources    and see what's enabled.

---

### Post by wolfen69 on 2007-07-22
```
gksudo gedit /etc/apt/sources.list
```
then remove any "#" that comes before a line that starts with "deb". save file, then:
```
sudo apt-get update
```

you may also want medibuntu repos, for extra packages    [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

---

### Post by funkshun on 2007-07-22
> **wolfen69 said:**
> it's in synaptic for me. go to system>admin.>software sources    and see what's enabled.

All I have is system>admin>software properties. I check in there and could not find anything.
I also used sysnaptics and could not find the file either. It's dowloaded onto my desktop. I looking at the file right now.

---

### Post by wolfen69 on 2007-07-22
try what i said the previous 2 posts. especially the sources.list and medibuntu.

---

### Post by funkshun on 2007-07-22
Thanks it worked. It's most appriciated.

---

