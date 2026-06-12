---
title: "Compiling and altering software"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by blittle on 2007-07-31
I guess what I need to know is when is it appropriate to compile software in order for iot to work with your hardware?
The reason for my question is this:
I'm running a Dell 1501 with 64-bit AMD processor. I forgot that a new 64-bit chip might may be the big fat factor as to why some program will not install or run properly, or at least I'm guessing that that is the case.
My problem so far is only one: I cannot get this one program called Levelator to install on my machine. It comes with python 2.5 and the makers say it works with Feisty. Yet, if I run "./" nothing happens. The software does not come with documentation and I have not gotten any response to my emails or the forum on Gigavox asking for help. If I need to (re)complile the software to get it to work, what would be the best method on how to start? There seems to be a lot of info on the subject, but I don't know where to start.

Thanks.

---

### Post by shagster_ on 2007-07-31
you're not just typing "./" in the command line, are you? you should be able to just run
```
> ./levelator
```
in the untarred directory

do you have the latest packages of python? (sudo apt-get install python2.5)
[http://packages.ubuntu.com/feisty/python/python]("http://packages.ubuntu.com/feisty/python/python")

---

### Post by rich.bradshaw on 2007-07-31
64 bit will only make a difference if you installed the 64bit version of ubuntu, it won't matter otherwise.

---

### Post by rich.bradshaw on 2007-07-31
Not that you should assume that's the problem anyway, just that that's the only time it matters!

---

### Post by blittle on 2007-07-31
> **rich.bradshaw said:**
> Not that you should assume that's the problem anyway, just that that's the only time it matters!
 I am running Fiesty for 64-bit.

Thank you.

---

### Post by blittle on 2007-07-31
> **shagster_ said:**
> you're not just typing "./" in the command line, are you? you should be able to just run
```
> ./levelator
```
in the untarred directory

do you have the latest packages of python? (sudo apt-get install python2.5)
[http://packages.ubuntu.com/feisty/python/python]("http://packages.ubuntu.com/feisty/python/python")

Yes, terminal says that I have the latest verion of python (2.5) installed. 0 upgraded.
When I've run "./levelator", I get a "logging to  /tmp/uploader.log" response. Then cursor continues as in in untarred directory.
Sorry meant to type that I ran "./levelator" in past attempts.

---

### Post by blittle on 2007-07-31
From the uploader.log file:

INFO; __init__; 1319:  logging...                               
INFO; __init__; 1319:  Traceback (most recent call last):
      
INFO; __init__; 1319:    File "main.py", line 2, in <module>
   
INFO; __init__; 1319:                                           
INFO; __init__; 1319:  import gui
                              
INFO; __init__; 1319:    File "/home/norman/code/levelator/gui/__init__.py", line 9, in <module>
 
INFO; __init__; 1319:    File "/home/norman/code/levelator/gui/main_window_linux.py", line 5, in <module>
 
INFO; __init__; 1319:    File "/home/norman/code/levelator/gui/main_window.py", line 1, in <module>
 
INFO; __init__; 1319:  ImportError                              
INFO; __init__; 1319:  :                                        
INFO; __init__; 1319:  No module named wx                       
INFO; __init__; 1319:

This couldbe a directory issue. Will investigate further...

---

### Post by Bachstelze on 2007-07-31
> Linux

    * Built and tested on Ubuntu
    * Requires Python **and wxPython**
    * Download The Levelator for Ubuntu Edgy Eft (Python 2.4)
    * Download The Levelator for Ubuntu Feisty Faun (Python 2.5)
    * Help/support for Linux users
    * Latest build: 1746


You must read the docs more carefully...

---

### Post by asmoore82 on 2007-07-31
The Levelator is *NOT* Free Software.

---

### Post by shagster_ on 2007-07-31
from their website [http://www.gigavox.com/levelator](http://www.gigavox.com/levelator)
> Do you believe in magic? You will after using The Levelator to enhance your podcast. And you'll be amazed that it's free (for non-commercial use).
?

and if you haven't already, 
[http://wiki.wxpython.org/InstallingOnUbuntuOrDebian]("http://wiki.wxpython.org/InstallingOnUbuntuOrDebian")

---

### Post by Nekiruhs on 2007-07-31
> **shagster_ said:**
> from their website [http://www.gigavox.com/levelator](http://www.gigavox.com/levelator)

?

and if you haven't already, 
[http://wiki.wxpython.org/InstallingOnUbuntuOrDebian]("http://wiki.wxpython.org/InstallingOnUbuntuOrDebian")
What he means is free as in speech, not as in beer.

---

### Post by blittle on 2007-07-31
Thank you. I guess after looking for an actual doc on the page I didn't see the wxpython part right next to Python 2.5 cation. I guess I thought it was part of the regular python package.
Anyway, I installed wxpython and Levelator came up! the only problem now is that in the process of generating the leveled file I get this message: 

"./level: error while loading shared libraries:libFLAC.so.7: cannot open shared object file: NO such file or directory\n"

I found libflac7_1.1.2-6amd64.deb and it installed without issues, but I still get the message. I will continue to figure this out. But very greatful for the help so far.

---

