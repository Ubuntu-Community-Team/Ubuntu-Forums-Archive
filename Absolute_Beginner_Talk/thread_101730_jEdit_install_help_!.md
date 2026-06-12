---
title: "jEdit install help !"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by hobnobsandtea on 2005-12-10
As of today I am 100% Ubuntu Laptop user !!!

anyhow joy aside, how do i install jEdit on ubuntu breezy badger?

---

### Post by Leif on 2005-12-10
from the installation instructions at their homepage :

sudo gedit /etc/apt/sources.list

add to the end :

```

deb http://dl.sourceforge.net/sourceforge/jedit ./
deb-src http://dl.sourceforge.net/sourceforge/jedit ./

```

save & close

sudo apt-get update
sudo apt-get install jedit

---

### Post by hobnobsandtea on 2005-12-10
thank you very much thats great !!!

---

### Post by Zdravko on 2006-03-04
After the install, nothing happens. The Program never starts when I click on its menu. Do I need to install something additional?

---

### Post by WelterPelter on 2006-03-04
I hesitate to ask this, but do you have java installed?

---

### Post by Zdravko on 2006-03-04
Nope. But I am downloading Eclipse now... I hope there will be Java also... :(

---

### Post by Sandlst on 2006-03-04
one way of finding out why a menu item will not launch, is to right click on the icon, selecting 'copy to desktop' right clicking on the new desktop icon, select properties, go to launcher tab, copy the whole line listed as 'Command' open a terminal, paste, hit enter and hopefully it will give you an error msg.

---

### Post by Zdravko on 2006-03-04
> 
zdravko@c86-109:~$ jedit %U
GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!
Exception in thread "main" java.lang.OutOfMemoryError
   <<No stacktrace available>>

This is the error.

---

### Post by WelterPelter on 2006-03-04
[QUOTE=Zdravko]Nope. But I am downloading Eclipse now... I hope there will be Java also... :([/QUOTE]

You can install java for your system either through Synaptic (which will get you version 1.4.2), or through Automatix (version 1.5).

There are other ways, but these are the easiest. Once you install java, jEdit will run just fine.

Let me know if you need help with Synaptic or Automatix.

---

### Post by Zdravko on 2006-03-04
Phew, 60MB for just a Java?! Anyway, I will download it...

---

### Post by WelterPelter on 2006-03-04
[QUOTE=Zdravko]Phew, 60MB for just a Java?! Anyway, I will download it...[/QUOTE]

Which way are you doing it?

---

### Post by Zdravko on 2006-03-04
With Synaptic. Why? It installed and then everything was OK. jEdit is quite too complex for C++ programming - I have to invoke the compiler by myself?

---

### Post by WelterPelter on 2006-03-04
[QUOTE=Zdravko]With Synaptic. Why? It installed and then everything was OK. jEdit is quite too complex for C++ programming - I have to invoke the compiler by myself?[/QUOTE]

Actually, it's quite simple. jEdit is a fabulous editor. It has a lot of plugins and possible configurations, but in the end, it's still basically an editor, with some expanded capacities. It sounds like you want an IDE -- something quite a bit more complicated. Sorry I can't recommend one for C++ programming. I'm sure there are zillions of C++ forums where you can dig into that question.

---

