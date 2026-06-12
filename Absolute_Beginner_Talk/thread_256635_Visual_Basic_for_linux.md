---
title: "Visual Basic for linux?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-09-13
I love visual basic 2005. Is there any VB coding apps for linux?
(Preferably not VB6 language. I need 2005. ;) Or is there any graphical C++ apps?

---

### Post by Lord Illidan on 2006-09-13
Gambas should take care of your visual basic needs.

As for graphical c++...either GTK+ or QT should fit the bill.

---

### Post by jdong on 2006-09-13
Monodevelop (a older version is available in Dapper, good for previewing) is probably closest to what you're looking for. It's an IDE for Mono, which is basically .NET for Linux. In the upcoming Edgy Eft release of Ubuntu, a newer Monodevelop with a graphical (drag-and-drop) GUI designer for the C# language is available (I don't think it does VB.Net yet, sadly), which should suit your needs .

---

### Post by Ben Sprinkle on 2006-09-13
Yeah, I do not want .NET, hate it. I am looking for a VB app for linux that is the 2005 language, not any other. Also, does these vb apps even work on linux, or is it different code.

---

### Post by cstudent on 2006-09-13
There is also Real Basic.

[http://www.realsoftware.com/](http://www.realsoftware.com/)


This software was written with it:

[http://www.floola.com/modules/wiwimod/index.php?page=WiwiHome](http://www.floola.com/modules/wiwimod/index.php?page=WiwiHome)

---

### Post by jdong on 2006-09-13
Is visual basic 2005 not a .NET language?

And to answer your compatibility question, no, binaries  will not run on both Windows and Linux. The language syntax may be similar but the output programs will not run on both platform. You might stand a slight chance of SIMPLE mono apps running under Windows (a better chance with GTK# if you install GTK# on the target Windows machines), but don't hold out much hope.

---

### Post by Ben Sprinkle on 2006-09-13
Alright, I am liking monodevelop. It says it is mainly for C#, does the GUI part of monodevelop also work for VB 2005 language?

---

### Post by jdong on 2006-09-13
Unfortunately I don't think the GUI designer works for the Visual Basic language (yet). Sorry :(


OTOH, C# really isn't a bad language :)

---

### Post by Ben Sprinkle on 2006-09-13
Just got home from school, I will start C# I heard it is faster in speed then C++. I will use msdn forums for help, thanks.

---

### Post by jdong on 2006-09-13
> **Goat Spirit said:**
> Just got home from school, I will start C# I heard it is faster in speed then C++. I will use msdn forums for help, thanks.

Well, be careful there ;) C# will not perform as well as C++ in terms of raw speeds, but for most tasks it's not anything you'd ever notice. C# is faster to learn and be productive in than C++ for sure :). A lot of the syntax overlaps between C# and C++, and combining that with your existing VB knowledge (which should make you quite familar with the .NET class library), you should be able to be up and running in C# in just minutes or hours :)

---

