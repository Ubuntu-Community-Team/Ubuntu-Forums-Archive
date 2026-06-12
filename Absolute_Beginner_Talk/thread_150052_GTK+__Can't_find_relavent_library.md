---
title: "GTK+ ???? Can't find relavent library"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by belikralj on 2006-03-25
I have just started to learn to program GUI applications in C, so I will most likely need the GTK+ library or headers or something, but having searched synaptic and installing many, GTK+ related libraries I couldn't find THE GTK+ library. Please help!

I already have g++, gcc, gjc, gcj.... for Java, C++, and C code compilation.

---

### Post by ComplexNumber on 2006-03-25
make sure you get the 'devel' packages.

---

### Post by belikralj on 2006-03-25
I have Ubuntu installed, so how can I check what exactly I have and what I need to install? Because I went through synaptic downloading almost everything that had GTK and/or C or C++ keywords.

---

### Post by ComplexNumber on 2006-03-25
how do you know that you have a particular package 'missing'?

---

### Post by belikralj on 2006-03-25
I don't, but in the book I'm learning C from it says to check for GTK+ by typing "gtk -config" which when I do returns "command not found".

---

### Post by Chyper on 2006-03-25
opps

---

### Post by ComplexNumber on 2006-03-25
[quote=belikralj]I don't, but in the book I'm learning C from it says to check for GTK+ by typing "gtk -config" which when I do returns "command not found".[/quote] thats because you typed it incorrectly. its gtk-config. there is NO space inbetween "gtk"  and "-config".

btw install a package called bash-completion because its really useful. i just typed "gtk" then hit the tab button and it brought up all the options, one of which was "gtk-config"

---

### Post by belikralj on 2006-03-25
Typing it in correctly fixed it. I feel a bit silly not seeing that before.

Thanx very much, I will get bash-completion as soon as my updates complete!

---

