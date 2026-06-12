---
title: "when/why would i use virtual terminal?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by shmengie on 2007-12-02
so, i'm still very green using linux. but, i'm reading as much as i can and playing around, trying to learn by doing. so, as you all know, there's these virtual terminals (ctrl+alt+f1-f6) that bring up just a terminal window (terminal session? maybe that's more accurate). why would i use that as opposed to gnome-terminal? and how the freakin' heck to i get back to the desktop? i tried ctrl+alt+bckspc and "gdm restart", ultimately having to ctrl+alt+del to restart the system and get back to my gui.

i assume the vt's are for compiling in the background and stuff like that, right?

thx!

---

### Post by Dr Small on 2007-12-02
Virtual Terminals can be used for starting multiple X displays on different terminals, and are very useful if X will not start and you have no GUI.

To get back to your desktop, press CTRL + ALT + F7
F7 is usually the default terminal where your GUI is.

Dr Small

---

### Post by shmengie on 2007-12-02
well, that was painless. thx!

---

### Post by Keith Hedger on 2007-12-02
u can also use the virtual terminals to kill off or renice misbehaving apps that are stopping the gui from working.

---

### Post by Dr Small on 2007-12-02
Here is my tutorial on how to start multiple X sessions with Virtual Terminals:
[http://php.8ez.com/drsmall/blog/?p=110](http://php.8ez.com/drsmall/blog/?p=110)

---

