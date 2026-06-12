---
title: "A start up error (error starting Genome setting Deamon)"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by almasry on 2007-02-17
Now , I am facing a big problem with my Ubuntu ..
The system is very very slow ..
and an error comes when it starts saying :  

> 
There was an error starting the Genome setting Deamon

Some thing such as themes , backgrounds and sounds may not work correctly 

Unable to determine the adress mesasage of the bus ......... etc 



even though I  logged to the Genome session in the start options , the problem remains appearing and the system is very very slow

how to fix this bug ???

---

### Post by almasry on 2007-02-18
No answer ...
that's goood ...
I will format and re-install ..

---

### Post by haricharan on 2007-02-18
you have to identify the cause of the problem....from when did it start.....did you install something? or edit some files?
Can you please elaborate on the problem??

---

### Post by jordanmthomas on 2007-02-18
try this:
```
rm ~/.gtkrc*
```

Sometimes KDE will add its own .gtkrc and Gnome gets angry.  Then, log out of your gnome-session and log back in to see if the problem persists.

---

### Post by almasry on 2007-02-24
I didn't install KDE , and i think it is not installed by default .. my version is 6.10 (ubuntu)..
this error was after i was setting up some new softs and my pc hanged , and i forced it to restart from the restart button ...

---

