---
title: "Un-installing...?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by grahamroese on 2006-07-12
Obsessive-compulsive disorder is keeping me from keeping two or more applications that serve the same purpose (i.e. Thunderbird and Evolution e-mail clients). I find myself staring at all of my package managers, not knowing what to do, with the intent of uninstalling all of my functional duplicates... So I ask...:

How do I do this easily?

---

### Post by slimdog360 on 2006-07-12
[http://www.marzocca.net/linux/gtkorphan.html]("http://www.marzocca.net/linux/gtkorphan.html")
thats a good program, it gets rid of the unused dependencies also.

---

### Post by ncappel1 on 2006-07-12
The easiest way is through the Synaptic Package Manager, but be careful, you don't want to remove the files that both programs share. Or else it won't work.

anyone else have more input?

---

### Post by aysiu on 2006-07-12
If you remove a program that both files share, you'll be warned that it's going to uninstall both programs.

---

### Post by Qrk on 2006-07-12
another great tip is to use aptitude (not synaptic) to install programs because it will remove  dependencies when you remove the program. The syntax is the same as apt-get,

sudo aptitude install packagename

---

### Post by aysiu on 2006-07-12
I believe *aptitude* functions properly if you do an update first. ```
sudo aptitude update
sudo aptitude install packagename
``` [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by bruenig on 2006-07-12
```
sudo apt-get remove name
```
do that to whatever you don't want

---

