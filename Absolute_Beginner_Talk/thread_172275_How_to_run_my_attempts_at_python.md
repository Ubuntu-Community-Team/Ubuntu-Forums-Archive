---
title: "How to run my attempts at python"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by t6bill on 2006-05-08
Hi,
I just got online with my Ubuntu box a day or so ago.  I installed Idle for python using apt-get.  I'm confused on how to run my python programs, and where to save them.  I'm using a beginner book that gives instructions mainly for windows, but cannot seem to "run" my programs in Ubuntu.  In Windows, all I have to do is double-click on the icon of the saved program.  Would greatly appreciate any help--I'm a real newbie both at ubuntu and python.
t6bill

---

### Post by sYs^ on 2006-05-08
Imho, you should try this: python xxxx.pl or something like this :p

---

### Post by Omnios on 2006-05-08
I use SPE , (Stani's Python Editor) I think it is available from SYnaptic.

---

### Post by Kvark on 2006-05-08
Right click on a .py file and choose "open with another program...". Then click "use a custom command" at the bottom of the window that popped up and type "python". After doing that once you can right click on .py files and choose "open with python".

It is often useful to run the programs in a terminal to see any error messages and other output. The command to use is the same as the "custom command" you added to right click so just type "cd path/to/your/python/programs" followed by "python file.py".

---

### Post by Bloch on 2006-05-08
Save your python program with the .py extension. 
Now open a terminal and move to the directory where your program is stored. (You know you can move a folder onto the terminal, and the full path to that folder appears in the terminal. So you can juts write 
cd
at the bash prompt and click and drag the folder onto the terminal, and the directory path e.g. /home/bill/pythonstuff will appear)

To run type
python ****.py

Alternatively put this line as the first of the prog
#!/usr/bin/python2.4
Then set the permissions on the program to executable. Now click on it and choose "run in terminal"
This line is interpreted by the bash shell to mean "run /usr/bin/python2.4 on this file". Python starts up and is handed the file. Pythin interprets any line beginning with # as a comment, so will ignore this start-up line.

The problem is, the terminal window disappears when the program is finished (as it does in windows too) You might need
x=raw_input("Press Enter to finish")
as the last line. I hope you know enough Python to see what this does - it's a standard solution to keep the terminal window open until you press enter

---

### Post by Bloch on 2006-05-08
Kvark;
I was learning python and had already tried your solution. I tried it again just now. For some reason it does't work, though it sounds reasonable. It doesn't work no matter whether I use
python  or /usr/bin/python2.4

---

### Post by Kvark on 2006-05-08
Try typing just "python" in a terminal. You should see something like this:
```
$python
Python 2.4.2 (#2, Sep 30 2005, 21:19:01)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>
```
If that doesn't work then there is something wrong with your python installation. If "sudo apt-get install python" doesn't fix that then I have no idea.

At the >>> prompt you get to type python interactively. The only difference to running .py files is that you type one line at a time instead of the whole program on beforehand. Which is very good for randomly exploring python and is also one of the best calculators I've ever seen, at least it beats my TI-83 plus.

If it does work then try tying one of your programs from start to finish and see which lines you run into problems on. If it's at an "import..." line then you probably need to install some additional python package that your program depends on.

---

