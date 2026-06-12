---
title: "How to access programs created with make and make install"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by bamend on 2006-08-29
Okay.  I've untarred the file, config'ed it, ran "make", then sudo make install and everything works.  Where does the program go and how do I access it?  Is there a special directory you go to find it like in windows or what?

---

### Post by mustang on 2006-08-30
Typically most programs are installed in /usr/bin/

---

### Post by bodhi.zazen on 2006-08-30
> **bamend said:**
> Okay.  I've untarred the file, config'ed it, ran "make", then sudo make install and everything works.  Where does the program go and how do I access it?  Is there a special directory you go to find it like in windows or what?

I do not know what program you installed.
I will call it "program_name"

Try:

1. type the program name in a terminal
```
program_name
```
This will likely start the program.

2. To locate the program, again in a terminal type
```
which program_name
```
This should return something like /usr/bin/program_name

3. You can then edit the menu or add a launcher. In the box "run" enter the path returned in #2.

---

