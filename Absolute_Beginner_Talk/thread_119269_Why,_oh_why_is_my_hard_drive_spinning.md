---
title: "Why, oh why is my hard drive spinning?"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by mohapi on 2006-01-19
A quick question: Occasionally my hard drive starts spinning and accessing when there's nothing going on. I'm not downloading or surfing or playing music. ... So what's it after?

Is there a process monitor I can check? I feel like I should panic, after years of working with Windows and wondering what was messing with the drive while I wasn't watching.

---

### Post by purpleturtle on 2006-01-19
Maybe it is writing to your swap partition?

---

### Post by mohapi on 2006-01-19
I guess that's possible, although it usually happens while I'm typing, with nothing else going on. 

There can be only one explanation.

GREMLINS.

:p

---

### Post by codejunkie on 2006-01-19
when it's running open a terminal and enter ```
top
```and see if updatedb is listed that might be the cause of it. it's indexing the harddrive for the search function.

---

### Post by mohapi on 2006-01-19
Oooh! I like that. Helps support my illusion of control. :rolleyes: 

I don't see "updatedb", but I'll keep it open until I hear it chunking away again. Thanks for the help.

---

### Post by mohapi on 2006-01-20
Yup, that's what it was. I caught it accessing again and quickly started "top" in a terminal. At the top of the stack: updatedb. Caught red-handed.

Thanks for your help, folks. I promise not to panic next time. :)

---

### Post by hen3rz on 2006-01-20
> and see if updatedb is listed that might be the cause of it. it's indexing the harddrive for the search function.

What is updatedb?????

---

### Post by codejunkie on 2006-01-20
[QUOTE=hen3rz]What is updatedb?????[/QUOTE]
it indexes the harddrive for the search function.

---

### Post by crovax666 on 2006-01-20
[QUOTE=hen3rz]What is updatedb?????[/QUOTE]

try: man updatedb (or: info updatedb)

It makes a file database to allow quickly searching of files, its quite productive to look at those things yourself in the man pages. Especially if its as simple as this...

---

