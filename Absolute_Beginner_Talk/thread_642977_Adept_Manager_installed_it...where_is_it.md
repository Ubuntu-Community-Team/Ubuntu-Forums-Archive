---
title: "Adept Manager installed it...where is it?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by LarryJ2 on 2007-12-17
I typically find a program package I am interested in and ask Adept Manager to install it.  But now I'm faced with the question:  how to I run it and where is the documentation??

So typically the search begins... I look in the KMenu tree (I prefer KDE).... nothing there...

So I open a terminal window and  use  "sudo find / -name myapplication".  This takes a long time and a lot of typing...

Then I stumbled on the command "locate".   

Again in a terminal window  the command looks like
$ locate myapplication

Much quicker and automatically does  the search with wild cards so that all combinations of "myapplication"  (maybe myapplication.sh  or myapplication.doc)  are displayed.

"locate" must have arrived with one of the packages findutils, kio-locate, or slocate.  If locate in a terminal window gives up nothing,  try installing these packages.

After two years of Linux (first Fedora and now Ubuntu/Kubuntu) you'd think I wouldn't find anything new but here it is!  Linux is one amazing extraordinary OS.

LJ

---

### Post by chippy99 on 2007-12-17
Most applications will install a link in your menu but if not try using the whereis command.
i.e. whereis kate

---

