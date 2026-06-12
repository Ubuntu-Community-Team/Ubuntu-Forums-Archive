---
title: "Python"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-12-29
Greetings.
I have just downloaded the latest source for Python. I then did ./configure + make + make install and everything went great. However, when I double click my python apps, the source code comes up on the screen in kate. What step am I not performing here. I have never used python before, so please keep in mind I dont know what the obvious first steps would be to getting python working from source. 

Btw.. I am intentionally not using synaptic to install it because I want to know how to do it from the command line if I need to install it to a server.

Thanks!

---

### Post by Silentvoice on 2006-12-29
The reason why this is happening is because python is an interpreted language, in order for the source code files to execute by just double clicking them you must first add the line on the top
#/usr/bin/python
this is so your OS knows what is interpreting it(in this case, the python interpreter)

next you need to allow execute privileges. you can do this graphically (right click, go to permissions, check execute) however  I prefer the command line 
the command to change permissions on linux (or any UNIX variant)  is chmod (short for change mode)

chmod is a very powerful tool when it comes to your computer's security so for future reference here's the syntax of the command

chmod (users)+- (privileges) (file)
users are represented by three letters U, G, and O
U stands for USER (the user who OWNS the file, which should be you in this case)
G stands for GROUP or any group the user may be in
O stands for OTHERS (also called WORLD) which is anybody else (basically everybody)

the + or - is you are giving the stated users privileges or you are taking them away.

privileges are also in three letters, R, W , and X
R stands for READ
W stands for WRITE
X stands for EXECUTE

after you've added that top line, you're going to want to do the following chmod command

chmod u+x /path/of/python/file/python.py

so what you're doing essentially is telling the computer that you want USER to gain EXECUTABLE rights to python.py.

after you do this, you will get a message saying that this is an executable do you want to run in terminal display or run, click run in terminal 

also if that's annoying you can just do what I do, on the command line just type python, then add the file as an argument.. so python mypythonprogram.py

---

### Post by DirtDawg on 2006-12-29
Nevermind!

---

