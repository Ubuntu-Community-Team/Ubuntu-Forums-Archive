---
title: "What's supposed to be at the top of a script?"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-12-07
I used to run a backup script, which simply mounted my drive, rsync'd everything from my home directory to the drive, and then unmounted it.

At the top, what all is supposed to be there? I completely forget.

---

### Post by jordanmthomas on 2007-12-07
It depends on what you want to run the script with
Bash script:
```
#!/bin/bash
```
Python script:
```
#!/usr/bin/python
```
etc...

---

### Post by Roasted on 2007-12-11
bash sounds familiar. I plugged that in and the script is working now as we speak.

However, what's the difference from bash and python?

---

### Post by meatpan on 2007-12-11
I cut the description field from 'man bash' and 'man python':

Bash:   Bash  is an sh-compatible command language interpreter that executes commands read from the standard input or from  file.

Python: Python  is  an  interpreted, interactive, object-oriented programming language that combines remarkable power with very clear syntax.

---

