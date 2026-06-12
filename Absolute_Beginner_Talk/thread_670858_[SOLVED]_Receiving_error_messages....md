---
title: "[SOLVED] Receiving error messages..."
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Lisa Y on 2008-01-17
Hello everyone....

i had download blue proximit and hipo from getdeb.net...transfered them to my flash then to my laptop...when i clicked to install package....i see that there is an error...

For the Blueproximity i received the following error message:

Error: Dependency is not satisfiable: python-configobj

and for the hipo i received the following error message:

Error: Dependency is not satisfiable: libipoddevice0

please help....

-thanks !

---

### Post by cecure on 2008-01-17
You are missing the dependencies, go to System>Administrator>Synaptic Package Manager and check to see if you have the Dependencies (ie python-configobj) installed, if you dont try to install them.

Good Luck!

---

### Post by spiderbatdad on 2008-01-17
Those are a package and a library on which  the program you want to install depends. You can find python package in synaptic...not sure about the other. google it.

---

### Post by Lisa Y on 2008-01-18
ohhh ok....

so would downloading the Win32 extension clear the Python  error???

[http://starship.python.net/crew/mhammond/win32/Downloads.html](http://starship.python.net/crew/mhammond/win32/Downloads.html)

---

### Post by Christmas on 2008-01-18
Try this: open a Terminal or Konsole and type:
```
sudo apt-get install python-configobj libipoddevice0
```
Enter your user password (it goes in even if you see no output) and try installing your programs again.

---

### Post by Lisa Y on 2008-01-19
got it solved....

THANKSSS FOR ALL THE INFO!

---

