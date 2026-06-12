---
title: "How to write programs in Ubuntu?"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by sbasak on 2005-12-15
I like to develop small applications in Ubuntu. Is there any Visual Basic like development tool available in Ubuntu?

Also, if I create some "executable" file in Ubuntu, will it work in other versions of Linux?

---

### Post by Rinzwind on 2005-12-15
Look up **C**, **C++** inside your add packages. Those are the more commonly used. **Python** [http://www.python.org/](http://www.python.org/) [http://diveintopython.org/](http://diveintopython.org/) is used alot too. I bet if you search your system for .py you'll find a fair amount of them ;) 

2nd: it depends on how you code it doesn't it? :) 
If you look at debian and ubuntu: most times a debian package needs to be re-packed to be able to be used on ubuntu. So it's not a matter of coding that needs to work but installation method.

---

### Post by earobinson on 2005-12-15
If its C/++ your looking for check this out [http://www.ubuntuforums.org/showthread.php?t=102597](http://www.ubuntuforums.org/showthread.php?t=102597)

---

### Post by NotJustANewbie on 2005-12-15
[http://vb4linux.sf.net](http://vb4linux.sf.net) is quite old but it will probably do for what you want. VB is not meant for linux ;)

---

### Post by bscbrit on 2005-12-15
Depending on your level of software expertise, you might want to have a look at 'Gambas'.  There should be plenty of help for Gambas users, which you can find using Google.

---

### Post by sbasak on 2005-12-15
Gambas doesn't seem to offer a version for Ubuntu.

---

### Post by az on 2005-12-15
Glade makes gnome widgets and you can use python with it if you do not want to use C or C++.  You can use Mono (C#) with glade, too.

You can use other languages too.  You have a lot of choice.

Neat examples:

[http://nat.org/demos/gtksharp.html](http://nat.org/demos/gtksharp.html)

From [http://nat.org/demos/](http://nat.org/demos/)
made using vnc2swf.

---

### Post by bscbrit on 2005-12-15
gambas 1.0.3-1ubuntu1 is in my respository. Its in Development Universe.

---

### Post by Estariel on 2005-12-15
another vote for gambas

---

### Post by David Marrs on 2005-12-15
I also vote for gambas. I don't really see the point in recommending C, C++ or Python to someone who just asked for a language in the style of VB.

---

### Post by az on 2005-12-15
[QUOTE=David Marrs] I don't really see the point in recommending C, C++ or Python to someone who just asked for a language in the style of VB.[/QUOTE]


Well, the fact that gambas is similar to VB, but not compatible with it is one reason.  Another reason is that the fact that there is a big choice of development environments and tool available to linux is a strength.  You don't just habe the one.

Also, the question was in relation to ubuntu, and a lot of stuff is already made in Python in Ubuntu.  You are pretty much ready to go with the tools on the install cd.

Maybe bash and zenity is more appropriate for really small applications.  Just pointing that out.  Does windows have a similar combination of tools?

---

