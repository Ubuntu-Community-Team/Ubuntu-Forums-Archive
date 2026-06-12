---
title: "[SOLVED] How to access python files in Ubuntu"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Phiber_tek on 2007-12-04
I just installed Ubuntu 2 nights ago and think I've finally settled in with it, I've got Compiz working like a charm...I think, and everything is really fast and really smooth. So...now that I'm to that point I began to look for my apps, the main reason I installed Ubuntu was for the programming advantages; and I just started to learn Python about 2 nights ago (started reading the tutorial) on my XP machine.  I looked for it in all the app bars and all that at the top left but can't find anything about Python at all up there: command line interface, tutorials, libraries, nothing; yet in my hard-drive I do have a 'python' folder in etc., so 2 things really:

a) where is the base tutorial help package thing for Python

and 

b) does any one know of any other good training websites or programs or tutorials (note: I do learn best with interaction, so I like it when the tutorial has you try stuff out while you learn)

Thanks in advance for any help!

---

### Post by bloodniece on 2007-12-05
In Linux it is all about the man pages.

Open Gnome-Terminal
Applications --> Accessories --> Terminal
```
man python
```

I like the OReilly book: Python in a Nutshell

Sites:
[http://docs.python.org/tut/](http://docs.python.org/tut/)
[http://www.diveintopython.org/](http://www.diveintopython.org/)
Python Web Framework:[ http://www.djangoproject.com/]("http://www.djangoproject.com/")

---

### Post by LaRoza on 2007-12-05
Dive Into Python isn't for new programmers.

[http://laroza.pbwiki.com/Python](http://laroza.pbwiki.com/Python)

---

### Post by GGLucas on 2007-12-05
You create a text file (preferably with the .py extension), write "#!/usr/bin/env python" on the first line at the top, and start typing your Python code learned from all the nice tutorials, run it by going to the terminal and using "python myfile.py". That's the simplest way to execute python code I know of, gedit is nice for editing too.

---

### Post by The Cog on 2007-12-05
You create your python files with a text editor. By convention (but not a requirement), python files end in ".py". Editors that I use are gedit and geany. Geany is in the repositories. I always configure the editors to insert spaces instead of tabs - mixed tabs and spaces in python files is really bad news.

You can launch the python file from the command line like this:
**python test.py**
(or whatever it's called)

Or you can make the python file itself executable with these two steps:
1) add this line as the first line of the file:
#!/usr/bin/env python
2) Set the executable flag on the file with this command:
**chmod +x test.py**

---

### Post by master5o1 on 2007-12-05
BTW to exit a man page you type "q"

Bugged me for ages.

---

### Post by Phiber_tek on 2007-12-05
Alright thanks everyone for all the help I finally got it, one more question: when I do make a program, say I make like a little widget, can I give it an extension to run in llinux and say vista and everything else, is it just a matter of how you package it? Also is it possible to give your program a .exe ending and have another version with the ending of the executable in Linux? Thanks again!

---

