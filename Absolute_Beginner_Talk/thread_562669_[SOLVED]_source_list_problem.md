---
title: "[SOLVED] source list problem"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by just learning on 2007-09-29
can anyone help me with this i can't seem to follow instructions to get mac-menu applet iam following the instructions but keep getting this error E: Malformed line 58 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

if anyone can help that would be great thanks :confused:

---

### Post by bodhi.zazen on 2007-09-29
Can you post the output of :

```
cat -n /etc/apt/sources.list | grep 58
```

---

### Post by just learning on 2007-09-29
cat: /etc/apt/sources.lst: No such file or directory


i hope you ment in terminal anyhow that's what i got.  by the way how,  besides copying do you get that straight up and down symbol.

---

### Post by southernman on 2007-09-29
The correct code would be

> cat -n /etc/apt/sources.list | grep 58

The pipe, aka | on most US English keyboards is above the "enter" key... far right. It has the backslash normally "\" and caps down makes it the pipe "|"

---

### Post by just learning on 2007-09-29
58  deb [http://apt.tt-solutions.com/ubuntu/feisty](http://apt.tt-solutions.com/ubuntu/feisty) main


that's the ouput i get from the code from southernman. thanks for the symbol lesson southernman, i can now create a pipe |.:)

---

### Post by southernman on 2007-09-29
Open the file in nano

> sudo nano /etc/apt/sources.list

and put a space between ubuntu/ and feisty like so
> 
[http://apt.tt-solutions.com/ubuntu/](http://apt.tt-solutions.com/ubuntu/) feisty main

eh, now you can lay pipe all day/night, just as you've only drempt about! lol - horrible I know! :p

---

### Post by meborc on 2007-09-29
and if you don't know yet

to save file in nano - ctrl+O followed by ENTER (if you choose not to change the file path)
to exit - ctrl+X

---

### Post by just learning on 2007-09-29
that did the trick thanks alot southernman you kept a simple problem simple. :guitar:

---

### Post by southernman on 2007-09-29
> **just learning said:**
> that did the trick thanks alot southernman you kept a simple problem simple. :guitar:

Good news for sure. 

No... Thank you! :)

---

### Post by bodhi.zazen on 2007-09-29
> **southernman said:**
> The correct code would be ... 

Oops, sorry for the typo ...

/bodhi fixes his original post

---

