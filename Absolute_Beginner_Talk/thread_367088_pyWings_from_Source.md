---
title: "pyWings from Source"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-21
Well previous topic made by me wasa bit different, in that i couldrun by simply locating and runing the pywings.py file, her i wanna do it vai ./configure and make install, but this is what i get:

```

shoaibi@saber-rider:~$ mkdir pyWingS
shoaibi@saber-rider:~$ cd pyWingS/
shoaibi@saber-rider:~/pyWingS$ tar -xzvf ~/py*.tar.gz
BUGS
CHANGES
COPYING
COPYING.newwings
COPYRIGHT
CREDITS
CREDITS.newwings
icon.xbm
INSTALL
NEWS
pywings_engine.py
pywings_hlhtx_data.py
pywings_ifimages.py
pywings_interface_tkinter.py
pywings.py
pywings.pyw
README
smgLib/
smgLib/tkinter/
smgLib/tkinter/smgDialog.py
smgLib/tkinter/smgHtmlView.py
smgLib/tkinter/smgAbout.py
smgLib/tkinter/smgAnimate.py
smgLib/smgMiscString.py
smgTkLib/
smgTkLib/smgDialog.py
smgTkLib/smgHtmlView.py
smgTkLib/smgAbout.py
smgTkLib/smgAnimate.py
shoaibi@saber-rider:~/pyWingS$ ls
BUGS
CREDITS
pywings_engine.py
pywings.pyw
CHANGES
CREDITS.newwings
pywings_hlhtx_data.py
README
COPYING
icon.xbm
pywings_ifimages.py
smgLib
COPYING.newwings
INSTALL
pywings_interface_tkinter.py  smgTkLib
COPYRIGHT
NEWS
pywings.py
shoaibi@saber-rider:~/pyWingS$ ./configure
bash: ./configure: No such file or directory

```

i have all the required things installed like build-essential, linux-headers, python-tk, gtklib1.2, checkinstall and etc...

---

### Post by taurus on 2007-02-21
There is no configure so looks like you just run it from there.

```
./pywings.py
```
Or what does INSTALL say anyway?

```
more INSTALL
```

---

### Post by shoaibi on 2007-02-21
Solved, it wasn't a source package,

---

