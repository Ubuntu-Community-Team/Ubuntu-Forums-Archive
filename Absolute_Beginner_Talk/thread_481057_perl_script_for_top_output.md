---
title: "perl script for top output"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by diatribe on 2007-06-22
I would like either a perl or python script to run top and output the top 3 processes so I could have it run to a pipe menu in openbox, does anyone know how I would go about accomplishing this?  I do not know perl or python :(

---

### Post by ahvargas on 2007-06-22
You can use tail is a command . Try 
man top

---

### Post by ahvargas on 2007-06-22
pardon me try 
man tail

---

### Post by diatribe on 2007-06-22
that doesnt really accomplish what I am going for, it needs to be a script for the pipe menu to work, thanks though

---

### Post by ahvargas on 2007-06-22
sorry , i didn't read your post quite well. If you can be more acurrate in what your looking for i can help you more. Here is a little python script that i think it could help.


#!/usr/bin/python

import commands

top=commands.getoutput("top -n 1").split("\n")
for i in  range (7,10):
        print top[i]

---

### Post by diatribe on 2007-06-22
n/m that got it I appreciate it :D

---

