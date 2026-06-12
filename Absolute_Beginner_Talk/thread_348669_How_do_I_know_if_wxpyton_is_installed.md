---
title: "How do I know if wxpyton is installed?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by fsando on 2007-01-29
I want to run wikidpad [http://wikidpad.python-hosting.com/]("http://wikidpad.python-hosting.com/")
It's a small very efficient note-taking program. I have used it extensively in windows and most of my notes are kept there. It is written in python and the homepage says it should run on linux.
 It is supposed to run on linux but I get this error:```
~$ bash wikidpad.sh
Exception occurred during global exception handling:
Traceback (most recent call last):
  File "/usr/share/wikidpad/ExceptionLogger.py", line 52, in onException
    f = open(os.path.join(EL._exceptionDestDir, "WikidPad_Error.log"), "a")
IOError: [Errno 13] Permission denied: '/usr/share/wikidpad/WikidPad_Error.log'
Original exception:
Traceback (most recent call last):
  File "WikidPad.py", line 1, in ?
    import WikidPadStarter
  File "/usr/share/wikidpad/WikidPadStarter.py", line 33, in ?
    from wxPython.wx import wxApp, wxMessageDialog, wxDEFAULT_FRAME_STYLE, \
ImportError: No module named wxPython.wx

```Program is installed/copied to ```
/usr/share/wikidpad/
```
the wikidpad.sh file:```
#!/bin/sh 
cd /usr/share/wikidpad
export PYTHONPATH=lib
python WikidPad.py

```I guess wxpython is not installed here - and a search in synaptics does not show a specific 'wxPython' packaged (a good handful of other apparently related stuff turns up).
A package 'python-wxversion' could be the one I'm looking for - but I'm not really too keen on trying new things out (spent half weekend cleaning after another hasty install).

---

### Post by Jussi Kukkonen on 2007-01-29
Debian packages are not always named like upstream wants...

***apt-cache show python-wxgtk2.6*** will tell you that the package replaces *wxpython2.6-0* and provides *python-wx*. Should be close enough?

---

### Post by fsando on 2007-01-29
Thanks!
It helped - I used synaptics to install python-wxgtk2.6

Wikidpad now starts - only got a permission problem.
I put wikidpad in /usr/share/wikidpad, it apparently needs to write to a database there which permissions don't allow (except if started by sudo).
I'm not sure how to go about it - I could move the whole thing to my home folder. On the other hand all other programs live happily in /usr/share/ and have no permissions problems. Anyway it's a problem for another thread, if it's not as easy as I think.

---

