---
title: "Softwares"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2006-11-26
I wanna use Matlab, Visual Studio 6, Microsoft SQL sever 2000, how do i do it? and also i have made LAMP, will it effect SQL Server installation?

---

### Post by Mr Fat Bat on 2006-11-26
have you tried using Wine?  I've run office apps in it.  It should run matlab.  If I were you and running all those win apps i'd use VMware to create a virtual machine and do it that way, visual studio has heeps of dependecies needed to compile some apps and I don't think Wine would handle it.  The more I think about it the more I reckon you should use a virtual machine, expecially when it comes to writing win apps.

---

### Post by Peepsalot on 2006-11-26
What sort of development are you doing in Visual Studio?   Maybe there is an alternative program that is native to linux.  Microsoft certainly isn't gonig to make a Linux version of these products.  I don't really understand why someone would want to run a linux box just to put Microsoft Software on it.  Most people would use MySQL or Postgres on a linux box.

Maybe it can be done through wine, but I've never heard of anyone doing it and it would most likely suffer performance greatly.  When you say SQL server 2000, do you want to actually run the server on the linux box, or do you just need to access it from the linux box, with something similar to SQL Server Enterprise Manager?

Matlab at least comes in a linux flavor, so you can just get that from the company themselves.  There are also some open source math applications that might have some of the same functionality as matlab, though I don't know much about them.  I think one of them is called octave.

---

### Post by shoaibi on 2006-11-28
I am developing using VC++ for the time being, but depending on time, i may need to develop in C3, just tell about VC++ for the time.
and i just couldn't understood what peepsalot said about SQL Server, i just want it to run as it used to on Windows. And what i wanna say other then that is i have done LAMP, now suppose if i install SQL server on wine [that is if it can be] will it effect on MySQL?

---

