---
title: "Installing JAVA"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by Scorpian831 on 2006-01-12
Hello I have had ubuntu on my computer for two days, so I am very new at this. I am having a problem installing java. Can anyone help me get it on my computer? I have a compaq PC that is about five years old.

Thank You to all

---

### Post by 23meg on 2006-01-12
See if [these instructions]("https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249") help you.

---

### Post by Cesium on 2006-01-12
If that doesn't work for you, you can try [automatix]("http://ubuntuforums.org/showthread.php?t=66563&highlight=automatix") to install Java.

---

### Post by bscbrit on 2006-01-14
Use Synaptic, and install j2re1.4.  Done!

---

### Post by Delkster on 2006-01-14
Personally, I believe that the easiest way (as in the most intuitive for the beginner) to install a Java Runtime Environment is to open `Add Applications' in the menu, searching for `java' and selecting Java Web Start for installation.

The result is the same as when installing with Synaptic or from the command line (as the wiki entry suggests) but gnome-app-install (which is launched from the aforementioned entry in the menu) is just so much simpler for these kinds of tasks. (Its search functionality could use some improvement, though.)

---

### Post by bscbrit on 2006-01-14
Whatever is your preference....  I use Synaptic hence my advice, but your way will also achieve the same aim.

I'm not sure I agree with your thoughts on 'intuitive' - but that is not the point of this thread. :D

---

### Post by simber on 2006-01-14
if you want the latest java, do the following :

open a terminal and type :

sudo gedit /etc/apt/sources.list

copy this 2 lines to the file :

deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free

now type :

sudo apt-get update

sudo apt-get install sun-j2re1.5

and that will do it

---

### Post by shplog on 2007-11-07
> **simber said:**
> if you want the latest java, do the following :

open a terminal and type :

sudo gedit /etc/apt/sources.list

"COMMAND NOT FOUND"

---

