---
title: "wine"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by frenchsquared on 2008-01-01
Ive been to the wine site and am even more confused

I have scene magazines with images of xp running inside linux

 Can I install the entire OS?
I want to install vista completely.
then install software inside the virtual Vista?

if so how?

sorry I have googled this but am even more confused

---

### Post by dr.silly on 2008-01-01
wine just runs a single programs not the whole shebang. use VirtualBox or VMware, etc. emulators.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by dr.silly on 2008-01-01
oh yes possible in it's own little window

---

### Post by peitschie on 2008-01-01
To add some more clarification to dr. silly's posts...

Wine "pretends" to be Windows to programs that you would usually run in Windows (such as Microsoft office, notepad etc.).  This allows you to install the programs and run them from linux.  It doesn't allow you to install Windows as this would make no sense... after all, you dont install Windows on Windows without using a technique called "virtualisation".

Virtualisation allows you to run a pretend computer inside your current OS (Ubuntu for example).  This means you can load up your virtualisation program (such as VirtualBox), and install Windows Vista or XP on your virtual computer.  This then gives you the full boot screen and everything.

So, to recap, wine is NOT Windows, and only provides the ability to run Windows .exe files and install Windows-based programs under Linux.  Virtualisation software such as VirtualBox creates a virtual computer, which you then can install Windows Vista on, and have Vista run in its own window.

---

### Post by frenchsquared on 2008-01-02
thank you,
 that should work for what i want

---

