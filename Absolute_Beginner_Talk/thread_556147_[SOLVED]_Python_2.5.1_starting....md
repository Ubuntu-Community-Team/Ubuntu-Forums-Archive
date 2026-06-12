---
title: "[SOLVED] Python 2.5.1 starting..."
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Tierial on 2007-09-20
So I'm somewhat new to python still. I used to use Visual Basic on Windows, then started teaching myself Python through the Python Shell in windows.

Problem is, I want to start using Python on Linux to do it now since I'm not using my windows machine... however, I'm confusing the hell out of myself.

The windows Shell would open up, and you'd go to open New or whatnot, and it would open a new box and you'd just type all the coding into there, and then save it, and be able to run it as a script.

In linux... I open Python (which is set up properly of course, because its preinstalled 2.5.1) and I get lost; Starting with how it opens through Terminal. Theres no choice to open a new window, you can type basic commands in, and its executes them after pressing Enter... (which I know python does in this window normally) ...but... what do I do? I don't really understand how to enter down, or how to use this at all... Is there some sort of guide in how to do this in Gnome Ubuntu 7.04 Feisty or something? I don't understand at all.


EDIT: I don't understand the concept of making the file. I think you can even make python in the Text Editor and just save it as a .py file? But how do I run this script on Linux?

---

### Post by finer recliner on 2007-09-21
if im interpreting you question correctly, you're unsure of how to write commands that take up more than one line.

in the python shell, if you type a command that ends in a ":" (or is simply expected to go on for more lines, the shell will display ... meaning you can enter in more commands until you hit enter twice

```

>>> print "hello"                             #single line command
hello
>>> for i in range(0,5):                   #multi line command
...     print i                                    #dont forget to indent this line
...                                                  #press enter twice when done.
0
1
2
3
4
>>> 

```

save a plaint text file as a .py with your favorite text editor. to run it, simply type the following in a terminal window (not python shell)
```

python filename.py

```

done!

hope this helps

---

### Post by Lord Illidan on 2007-09-21
Python has an interactive shell, the one you've found out by running ```
python
``` in the terminal.

It can also "parse" files.

So, if you open up gedit and paste :

```
       print "Hello, World!"
```

and save it as hello.py, you can then navigate there with the terminal and run ```
python hello.py
```

You can also use an IDE like geany (in the repositories) to make your work easier.

---

### Post by adwatkin19 on 2007-09-21
I didnt like using python straight through the terminal

instead i installed PythonCard from Synaptic

then created a launcher on my desktop for it

in PythonCard there is a coding window with the line numbers etc and you can open the shell window as well. 

I found out about this from the Beginning Python book that i have

Hope this helps

Adam

---

### Post by Tierial on 2007-09-21
All your answers are wonderfully helpful.
Sorry my question was a bit vague but I was overtired and it was just starting to bother me a quite bit.

I'm going to try all this in a few.


EDIT: how do I go about using that PythonCard? I  downloaded and install it through Synaptics.. now what? It made a folder in /usr/share/doc/pythoncard    aaaaaaaaand... I don't understand how to set it up.

---

### Post by adwatkin19 on 2007-09-21
To get it up and running:

right click the desktop and choose create launcher

Name it what ever you want, but in the command box type in: CodeEditor

No spaces or anything and then click OK. 

Double click the Icon and a code editor will appear. In here you can type your code and save it as a .py file or if you click on Shell > Shell window

then pretty much what you would get to through terminal is there for you to use. 

For more advanced info you can google it, or download the Beginning Python E-book and that will give you more information. 

Hope that helps

Adam

---

