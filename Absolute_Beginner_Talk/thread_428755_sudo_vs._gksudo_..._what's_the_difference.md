---
title: "sudo vs. gksudo ... what's the difference?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by mijj on 2007-04-30
I've seen abstract definitions that make no sense to a novice like myself.

I've seen examples where sudo and gksudo are used to launch gedit ... which is the one yer supposed to lauch gedit with - and why would it make a difference?

---

### Post by jfinkels on 2007-04-30
> **mijj said:**
> I've seen abstract definitions that make no sense to a novice like myself.

I've seen sudo and gksudo to launch gedit ... which is the one yer supposed to lauch gedit with?
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by Seisen on 2007-04-30
Its better to use gksude to launch gedit and any other graphical applications.

---

### Post by jvc26 on 2007-04-30
As the link jfinkels provides points out, for graphical applications it is very important you use gksudo due to the risks involved.
Il

---

### Post by ajgreeny on 2007-04-30
Have a look here:-
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
There is info here on the possible, if not likely, problems that can ensue if you use sudo for GUI programs.

---

### Post by mijj on 2007-05-02
so .. presumably (correct me if i've oversimplified things) ... if the command opens a window, then you use gksudo ... ? ... if it's all within the terminal .. you use sudo?

---

### Post by aysiu on 2007-05-02
> **mijj said:**
> so .. presumably (correct me if i've oversimplified things) ... if the command opens a window, then you use gksudo ... ? ... if it's all within the terminal .. you use sudo?
That's a good way to sum it up.

---

### Post by octoberdan on 2007-05-02
> **mijj said:**
> so .. presumably (correct me if i've oversimplified things) ... if the command opens a window, then you use gksudo ... ? ... if it's all within the terminal .. you use sudo?

That's a good way to tell. For if it's opening a new window, then the programming is no longer running within the console and is hooking into X. 

**Note for KDE users**: You can use kdesu

---

### Post by Blofeld on 2007-09-05
Why use gksudo for graphical applications?  Allow me to quote:
"There are other times, though, when side effects can be as mild as Firefox extensions not sticking or as extreme as as not being able to log in any more because the permissions on your .ICEauthority changed.  These errors occur because sometimes when sudo launches an application, it launches with root privileges but uses the user's configuration file."
:popcorn:

---

### Post by rsambuca on 2007-09-05
> **Blofeld said:**
> Why use gksudo for graphical applications?  Allow me to quote:
"There are other times, though, when side effects can be as mild as Firefox extensions not sticking or as extreme as as not being able to log in any more because the permissions on your .ICEauthority changed.  These errors occur because sometimes when sudo launches an application, it launches with root privileges but uses the user's configuration file."
:popcorn:

Hey, thanks for quoting something that was linked to back in post #2!

---

### Post by Blofeld on 2007-09-05
So, here's the obvious corollary:  why not simply use gksudo to launch both command-line ***_and_*** graphical applications?

---

### Post by rsambuca on 2007-09-05
> **Blofeld said:**
> So, here's the obvious corollary:  why not simply use gksudo to launch both command-line ***_and_*** graphical applications?

Because the purpose of gksudo is to run commands that require root permissions without the need to run an X terminal emulator.

---

### Post by greymongrey on 2007-09-05
Why not just open a root terminal and use neither one?

---

