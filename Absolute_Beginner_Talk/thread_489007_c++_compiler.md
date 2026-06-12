---
title: "c++ compiler?"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by yahn on 2007-06-30
I don't know if anyone is familiar with Dev-C++, but that is what I used to use.  I was just wondering if Ubuntu comes with a C++ compiler and where I could find it if it does, and if anyone has any experience using Dev-C++ with Ubuntu?

---

### Post by nick24 on 2007-06-30
I am pretty sure every lunux comes preinstalled with gcc (GNU compiler collection). Just type in gcc -v to find out if it's installed and its version.

---

### Post by pyros on 2007-06-30
It's been a while since I checked on it, but I think the linux port of dev c++ stalled some time ago. were you just looking for a compiler, or an IDE?

---

### Post by pyros on 2007-06-30
Yeah, it looks like the kylix version never really got to a workable state. You may want to try the anjuta IDE instead.

---

### Post by loell on 2007-06-30
g++, to install install in the command line

 for c++ compiler only
```
sudo apt-get install g++
```



for the complete tools in C/C++ compiling

```
sudo apt-get install build-essential 
``` 

for IDE, there a handful of them,  there is** anjuta , code::blocks , eclipse , KDevelope**

---

### Post by yahn on 2007-06-30
I was looking for an IDE.  The problem is, I know C++ pretty well, but, for whatever reason, I can never figure out how to use a new IDE.  So can anyone suggest a simple IDE, possibly one that comes with an easy to follow documentation.

Thank you for the quick replies.  I appreciate it.

---

### Post by loell on 2007-06-30
anjuta IDE might be for you

---

### Post by pyros on 2007-06-30
yeah, I must say I miss it. if even I could use it, you know it's a simple ide. Have you tried anjuta?

docs here:
[http://anjuta.sourceforge.net/documentations/subpage/documents/C/anjuta-manual/anjuta-manual.html](http://anjuta.sourceforge.net/documentations/subpage/documents/C/anjuta-manual/anjuta-manual.html)

---

### Post by yahn on 2007-06-30
Ahh.  Thank you.  Anjuta was exactly what I was looking for.  It looks and feels almost exactly like Dev-C++.

---

