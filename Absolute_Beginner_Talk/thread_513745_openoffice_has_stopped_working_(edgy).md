---
title: "openoffice has stopped working (edgy)"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Charlie Wilkes on 2007-07-30
Here is the error message I get when I try to launch the word processor from a command line:

charlie@charlie-laptop:~$ ooffice -writer %U
/usr/lib/openoffice/program/javaldx: error while loading shared 
libraries: libuno_sal.so.3: cannot open shared object file: No such file 
or directory
/usr/lib/openoffice/program/soffice.bin: error while loading shared 
libraries: libvcl680li.so: cannot open shared object file: No such file 
or directory

I tried to reinstall everything related to openoffice, but got an error message saying I had a corrupted package.

Last time I tried to use the word processor, it worked fine... this is baffling.  Any help will be much appreciated.

Charlie

---

### Post by Damanther on 2007-07-30
Try using the reconfigure option in debpkg ?? Something like

debpkg reconfigure openoffice

---

### Post by oilchangeguy on 2007-07-30
> **Damanther said:**
> Try using the reconfigure option in debpkg ?? Something like

debpkg reconfigure openoffice

unless you're positive, there's no way i'd use a "something like" suggestion. and why are you using a command line to open writer anyway?

---

### Post by Charlie Wilkes on 2007-07-30
> **oilchangeguy said:**
> unless you're positive, there's no way i'd use a "something like" suggestion. and why are you using a command line to open writer anyway?

I used the command line because nothing happened when I tried to launch writer from the GUI, and I wanted to get some kind of clue about why it was not working.

Charlie

---

### Post by Hagar Delest on 2007-08-01
You should try to install the official version, see here : [[Ubuntu] Installing OOo on Debian and Co.](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759)

---

### Post by avik on 2007-08-01
Along the lines of what Damanther said, try reconfiguring the package:

```
sudo dpkg-reconfigure openoffice.org
```

---

### Post by Charlie Wilkes on 2007-08-06
> **Hagar de l'Est said:**
> You should try to install the official version, see here : [[Ubuntu] Installing OOo on Debian and Co.](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759)

OK, thank you very much.  It worked and now I have openoffice back on my system.

Charlie

---

### Post by tmas on 2007-10-24
I`ve got the same problem! cant figure it out :(

This is what terminal says:

** (process:5951): WARNING **: Unknown error forking main binary / abnormal early exit ...

Anyone??

---

