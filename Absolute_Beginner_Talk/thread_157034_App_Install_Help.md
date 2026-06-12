---
title: "App Install Help"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by landsg on 2006-04-08
Hello All:

I am a linux-newbie, but have managed to try several different distros so far, and really like Ubuntu the best.

I have installed 'wine' using:

apt-get install wine

Looks like it installed, but I cannot find where it is in the file system.  How can I run the program??

This happened with a couple of other apps as well.  I have looked around for them but so far have not found them.

---

### Post by christhemonkey on 2006-04-08
in a terminal type:
```
locate wine
```
This should give you a list of places with wine in them.
Should bring up something /usr/bin
If so it is (probably) installed, so you can just type:
```
wine /pat/to/whatever.exe
```

---

### Post by sYs^ on 2006-04-08
Open up a terminal and type:

wine random.exe

(random.exe = the .exe file you want to run)

edit: ups, I was slow, lol

---

### Post by ncappel1 on 2006-04-08
after installing wine, you may have to type
```
winecfg
``` to configure it.

---

