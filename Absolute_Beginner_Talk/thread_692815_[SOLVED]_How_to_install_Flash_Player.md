---
title: "[SOLVED] How to install Flash Player"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by DJRhubarb on 2008-02-10
I have downloaded Adobe Flash Player to watch videos on say You Tube using Mozilla but it tells me to install Flash, I Have downloaded it but how do I install it. I am running 7.10.

Thanks:)

---

### Post by jan quark on 2008-02-10
ok 

either use this code
```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```
or this guide
[http://laiconic.quotaless.com/tutorial3.html](http://laiconic.quotaless.com/tutorial3.html)

---

### Post by hopelessone on 2008-02-10
usually a bar will drop down under the toolbar,

just click that and it gives you two options to automatically install...

hope helps...

---

### Post by djbsteart1 on 2008-02-10
go to youtube to get the bar listed above. flashplayer is also listed i the repos

---

### Post by blackdragon1157 on 2008-02-10
Every time I try to install flash in firefox, the install fails, but firefox thinks it finished.  On the ?6? computers I've put flash on, I've always had to either get it through synaptic or (in the worst case) download manually from adobe.  Could just be my bad luck though :)

---

### Post by Nepherte on 2008-02-10
Just download the tar.gz file from the adobe flash site. Unpack the file, run the install script that is included (with root priviliges i think) and follow the instructions.

---

### Post by msayed2004 on 2008-02-10
There is a problem caused by Adobe related to flash installation, any way the solution is here -> [[SOLVED] Bug #173890 flashplugin-nonfree md5 mispatch support thread]("http://ubuntuforums.org/showthread.php?t=636397")

---

### Post by DJRhubarb on 2008-02-11
Thanks guys, it's all working now-it was a bug in Adobe Flash that didn't install it properly.

---

