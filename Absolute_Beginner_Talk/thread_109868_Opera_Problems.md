---
title: "Opera Problems"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by Deneb Algedi on 2005-12-29
I've installed Opera via Automatix but I can't start it.
When irun it in a terminal i get the following:
```
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
Segmentatie fout
```
What should I do?

---

### Post by Suger on 2005-12-29
The two first lines are just warnings, everyone gets them. The third one seems to indicate a memory problem. Is your hardware really old ? Else, try to reinstall opera.

---

### Post by Deneb Algedi on 2005-12-30
> The third one seems to indicate a memory problem. Is your hardware really old ?About 13 months(certainly not a problem)
> Else, try to reinstall opera.
I've done(+deleting the .opera folder in my personal folder) and i get the same error.

---

### Post by Madpilot on 2005-12-30
Another Automatix victim... bleh.

Opera should run fine in Ubuntu - but get the Breezy .deb direct from opera.com/download and install that. (I'm using it to write this, so yes, it does work!) :) 

Opera on Ubuntu information here: [https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

---

### Post by arnieboy on 2005-12-30
[QUOTE=Deneb Algedi]I've installed Opera via Automatix but I can't start it.
When irun it in a terminal i get the following:
```
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
Segmentatie fout
```
What should I do?[/QUOTE]
since u have already used automatix do the following:
```
sudo apt-get remove opera
sudo apt-get install opera-static
```

---

### Post by arnieboy on 2005-12-30
..

---

### Post by missmoondog on 2006-01-09
[QUOTE=arnieboy]since u have already used automatix do the following:
```
sudo apt-get remove opera
sudo apt-get install opera-static
```[/QUOTE]

had same error, for some reason, on this machine. i just installed opera via automatix on 3 machines yesterday and didn't have any problems. did what was suggested here, all is good. now that opera  installs to the applications/internet section like it's supposed to, opera will be my main browser in Ubuntu also. easily the best browser out there.

---

