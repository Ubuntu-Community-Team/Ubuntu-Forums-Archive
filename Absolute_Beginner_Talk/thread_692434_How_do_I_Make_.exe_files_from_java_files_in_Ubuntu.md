---
title: "How do I Make .exe files from java files in Ubuntu?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by spydon on 2008-02-09
Hi.
I need to make .exe files from .jar or .class files...
Does anyone know any good programs for Ubuntu?
Preferably open source.

---

### Post by neonum6 on 2008-02-09
I don't think that is possible to make a .exe from a java code

---

### Post by spydon on 2008-02-09
It is possible, that is all I know :P

---

### Post by neonum6 on 2008-02-09
with javac? try with readind the javac manual!

---

### Post by spydon on 2008-02-09
No, you can't do it with the usual j2sdk tools you need to have a 3rd part application :/.

---

### Post by neonum6 on 2008-02-09
however is intersting could make executable fils from java code...

---

### Post by spupy on 2008-02-09
You want to make exe? As in "Windows executable" or as in "single-file executable"?

---

### Post by spydon on 2008-02-09
Windows executable...

---

### Post by spupy on 2008-02-09
Well, i don't think anyone in his right mind would create/port java-to-exe packager for Linux. [-X
You have to check if any of the Windows ones can run under wine.

Anyway, if you are programing for Windows, why don't just do it under Windows? :-k

---

### Post by happysmileman on 2008-02-09
AFAIK GCJ can create **Linux** native binaries from java, it's an addon to GCC or something, but I don't see why there'd be a way to make Windows programs on Linux, and I don't think it exists, you'd probably need to be on windows for it.

But since javac would compile it into bytecode which will run on both Windows and Linux you could just use that, unless you for some reason REALLY need an EXE

---

### Post by neonum6 on 2008-02-10
> **happysmileman said:**
> AFAIK GCJ can create **Linux** native binaries from java, it's an addon to GCC 

intersting!

---

### Post by Abild on 2008-02-10
> **happysmileman said:**
> AFAIK GCJ can create **Linux** native binaries from java, it's an addon to GCC or something, but I don't see why there'd be a way to make Windows programs on Linux, and I don't think it exists, you'd probably need to be on windows for it. 

There is a way to do this actually. MinGW makes it possible to generate Windows binaries from Linux.

---

### Post by spydon on 2008-02-11
> **Abild said:**
> There is a way to do this actually. MinGW makes it possible to generate Windows binaries from Linux.

Do you have a link or something, I can't find anything about how to do it :S

---

### Post by jon_gunnar on 2008-02-11
> **spydon said:**
> Do you have a link or something, I can't find anything about how to do it :S

First hit in Google
[Here]("http://www.mingw.org/docs.shtml")

---

### Post by bump_ on 2008-02-11
I had jsmooth working under wine at one point. DOn't know if it does anymore.

Check it out here:
[http://jsmooth.sourceforge.net/](http://jsmooth.sourceforge.net/)

---

### Post by spydon on 2008-02-11
> **jon_gunnar said:**
> First hit in Google
[Here]("http://www.mingw.org/docs.shtml")

I can't find anything about java and .exe's there... :P

I found this one [jar2exe]("http://www.regexlab.com/en/jar2exe/"), but I can't get it to work :?

---

