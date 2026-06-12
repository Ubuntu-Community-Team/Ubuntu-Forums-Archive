---
title: "Running Mac applicatons on Linux"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by very_japi on 2008-01-24
I looked this up in google and all i get is How to run Linux on a Mac, i trying to do the exact opposite.

Is it possible to run Mac applications on Linux?

Im guessing it should be easier to run Mac o Linux than it is to run Windows on Linux, since mac and linux are both unix based.

Is it possible? however remotely?

---

### Post by Rhubarb on 2008-01-24
To the best of my knowledge, you can't run mac programs at all in linux.

---

### Post by Steveway on 2008-01-24
No, read the other 5000 threads about this that have been created in the past months.

---

### Post by Sef on 2008-01-24
> Im guessing it should be easier to run Mac o Linux than it is to run Windows on Linux, since mac and linux are both unix based.

Not necessarily.  Apple has a lot of proprietary software as part of the OSX system and applications from Apple and other companies.  I found this article about [Executor - using Mac applications under Linux]("http://www.heise.de/ix/artikel/E/1996/11/064/").

---

### Post by very_japi on 2008-01-24
So what is it that makes windows aplcations portable and Mac aplications unportable?

---

### Post by emarkd on 2008-01-24
Windows apps are not portable.  We can run some Windows apps in Linux thanks to Wine.  Wine attempts to recreate the win32 api on top of the Linux kernel, kind of tricking apps into thinking they're running on Windows.  Some apps work, some don't and it's probably always going to be that way because the Wine project is like shooting at a moving target.  Every time MS makes a change to Windows, Wine has to try to catch up.  And I'm sure you can guess that MS is *NOT* assisting Wine in the process.

You can find more information here:  [http://www.winehq.org/](http://www.winehq.org/)

---

