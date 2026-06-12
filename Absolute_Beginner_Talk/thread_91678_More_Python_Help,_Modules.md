---
title: "More Python Help, Modules"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by poloman2 on 2005-11-17
Hello everyone, well I have been using Linux for little less than 23 hours. So you can tell im a starter..
This is my problem, i have been working with python in windows XP, i usually copy/save  modules or my .py programs into C:\ python24\ in order to execute them  or import them. But im clueless about where to place my .py modules created in windows.
also i need to work with pythong, how do i use it in ubuntu..

thanx in advance.....

---

### Post by DJ_Max on 2005-11-17
You can excute Python files anywhere where allowed.

```
python file.py
```

OR

If you make the file executable, and place the appropiate shebang at the top of the file. *#!/usr/bin/env python*
```
chmod a+x file.py
./file.py
```

You can import system modules normally (they are in /usr/lib/python2.x). But in your application where you make custom modules, you can place them in the same directory and/or in a sub directory.

Do a little reading [http://python.org/doc/2.4.2/tut/tut.html](http://python.org/doc/2.4.2/tut/tut.html)

---

### Post by poloman2 on 2005-11-18
Thank you....
it defenetly helped!!!:)

---

### Post by poloman2 on 2005-11-18
i Have another question, in windows when I open  python, and I go File>New Window, and a separate blank window opens for me to type my code, when i want to run , i just press F5 and  it runs the code  in pyhton IDLE. 
is there an equivalent process in linux?? or should i donwload an editor??

---

### Post by Van_Gogh on 2005-11-18
I guess that depends on your taste, but here's what I do:

Firstly, I don't use IDLE, I write my code in whatever text editor I can find(that has syntax colaration, obviously) and then use iPython to run my code. iPython is like a jacked up version of the interactive prompt in IDLE. Very nice stuff. You'll find it in the repositories. So, if my script is in /home/terji/programming I type in iPython(start it by typng "iPython" at the command promt):

run ./programming/myScript.py

and iPython runs it, and in the case of bugs, gives me a very nice traceback of what went wrong. Try it, maybe you'll like it. For me it makes me much more productive, because it gives me a much better overview of my code than IDLE.

BTW, I don't think IDLE is installed by default in Ubuntu, but you could of course get it from the repositories. Also, it may not show up in the menu, but you can start it by typing IDLE in the command promt(I think, try pressing the TAB-key to make Linux complete the word).

---

