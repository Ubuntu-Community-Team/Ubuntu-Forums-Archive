---
title: "Installing pyWings from Source"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-18
I was installing pyWings from Source downloaded from sourceforge and here is what i get:

```

shoaibi@saber-rider:~$ LocalApps/pyWings/pywings.py
Traceback (most recent call last):
  File "LocalApps/pyWings/pywings.py", line 81, in ?
    CommandLineSwitches()
  File "LocalApps/pyWings/pywings.py", line 73, in CommandLineSwitches
    from Tkinter import TkVersion
  File "/usr/lib/python2.4/lib-tk/Tkinter.py", line 41, in ?
    raise ImportError, str(msg) + ', please install the python-tk package'
ImportError: No module named _tkinter, please install the python-tk package


```

I have installed build-essential and linux-headers and Python 2.4 is also installed in my system by Default along with Ubuntu Install.

---

### Post by Arby on 2007-02-19
```
 raise ImportError, str(msg) + ', please install the python-tk package'
ImportError: No module named _tkinter, please install the python-tk package
```

There's your problem. The package you are installing seems to depend on the python-tk module for python. I have no idea whether this is part of a default python install or not, have you checked whether that package is installed.

If not you can install it either through Synaptic or by typing the following on the commandline
```
sudo apt-get install python-tk
``` if the package is already installed then you should see the following as part of the output. ```
python-tk is already the newest version.
``` In which case we will need to think again.

Try doing the above then try installing pyWings again. Let us know what happens.

---

### Post by edoules on 2007-03-14
Wow! Thanks! That tip helped me too.

I actually googled the precise error message that my little python script was generating.

(School project)

- Ed

---

### Post by Arby on 2007-03-14
and the moral of the story is, error messages are there for a reason. Make use of them. :) 

Glad to have helped

---

