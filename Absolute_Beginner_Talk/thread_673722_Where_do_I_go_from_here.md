---
title: "Where do I go from here?"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by thom flora on 2008-01-20
In "Add/Remove...Other" I'm trying to install Macromedia Flash and Ubuntu Restricted Other. I keep getting this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What does this mean and how do I "run" anything, much less "report"?

Please help, as I'm trying to use the Internet like you normally would with Windows or Mac (i.e. Flash working on YouTube,etc.)

---

### Post by Kilz on 2008-01-20
> **thom flora said:**
> In "Add/Remove...Other" I'm trying to install Macromedia Flash and Ubuntu Restricted Other. I keep getting this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What does this mean and how do I "run" anything, much less "report"?

Please help, as I'm trying to use the Internet like you normally would with Windows or Mac (i.e. Flash working on YouTube,etc.)

Open a terminal and type in 
```
dpkg --configure -a
```
then hit enter to fix the issue it ran into

---

### Post by JoshuaRL on 2008-01-20
Right now the download and install for Flash is broken the best way is to go to their site and follow the first set of directions to install flash.

[http://ubuntuforums.org/showthread.php?t=653312](http://ubuntuforums.org/showthread.php?t=653312)

---

### Post by x02flash on 2008-01-20
It worked much easier for me when I downloaded the Flashplayer .tar from Adobe's website.

Once you get that, open a terminal and use the following codes to get it set up (save it to the desktop and extract it there for the sake of simplicity) 

```
cd /home/[username]/Desktop/[name of extracted folder]
```

then once you've done that

```
./flashplayer-installer
```

give it a minute, and it should set up fine

---

