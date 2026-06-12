---
title: "Screen video recording with Istanbul"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by ayed on 2007-03-03
Ok, I have to make a video recording of my screen for a short tutorial, I was using Istanbul, but suddenly it doesn't work. When I typed Istanbul in my terminal I got this:

ayed@ayed-desktop:~$ istanbul
/var/lib/python-support/python2.4/istanbul/main/screen.py:19: GtkWarning: Unable to locate theme engine in module_path: "pixmap",
  event_box = gtk.EventBox()


so whats going on, and how can I fix it?

---

### Post by carlosfocker on 2007-03-03
check out this thread [http://ubuntuforums.org/showthread.php?p=2070345](http://ubuntuforums.org/showthread.php?p=2070345)

---

### Post by ayed on 2007-03-03
> **carlosfocker said:**
> check out this thread [http://ubuntuforums.org/showthread.php?p=2070345](http://ubuntuforums.org/showthread.php?p=2070345)

It didn't work, now it just does this:

ayed@ayed-desktop:~$ istanbul

thats it, just blank
But this happened when I pressed a button:

ayed@ayed-desktop:~$ istanbul
Traceback (most recent call last):
  File "/usr/bin/istanbul", line 40, in ?
    sys.exit(main.main(sys.argv))
  File "/var/lib/python-support/python2.4/istanbul/main/main.py", line 86, in main
    gtk.main()
KeyboardInterrupt
ayed@ayed-desktop:~$

---

### Post by xcat442 on 2007-03-03
Hi, Mabey try XvidCap or RecordMyDesktop

XvidCap
[http://xvidcap.sourceforge.net/](http://xvidcap.sourceforge.net/)

[COLOR="Red"]sudo apt-get install xvidcap[/COLOR]


[COLOR="Red"]sudo apt-get install  recordMyDesktop[/COLOR]

RecordMyDesktop takes a little more computer resources to run. XvidCap is a little lighter on resources if you keep the selection window small, but none the less they both work pretty good.

Peace

---

### Post by chuckyp on 2007-03-03
Istanbul has always been very buggy for me.  Sometimes it will work fine and other when I click to stop the recording I receive no save window.  I then have to hunt down the ogg file in /tmp and save it myself.  I'm thinking of switching applications also.

---

### Post by ayed on 2007-03-04
I Get this when I try to install:
ayed@ayed-desktop:~$ sudo apt-get install xvidcap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xvidcap
ayed@ayed-desktop:~$ sudo apt-get install recordMyDesktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package recordMyDesktop

---

### Post by carlosfocker on 2007-03-28
Go to this link to download the deb package:

[http://sourceforge.net/project/downloading.php?group_id=81535&use_mirror=umn&filename=xvidcap_1.1.5rc1_i386.deb&24897357](http://sourceforge.net/project/downloading.php?group_id=81535&use_mirror=umn&filename=xvidcap_1.1.5rc1_i386.deb&24897357)

Then browse to the directory it download to with a terminal and type this (Change the file name accordingly)

```
sudo dpkg -i  xvidcap_1.1.5rc1_i386.deb  
```

---

### Post by lamalex on 2007-03-28
go into synaptic and search for it or do an apt-cache search

---

