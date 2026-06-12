---
title: "How do I find the Gnome version?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by cairnsww on 2007-02-28
How do I find the Gnome version number? (This is on a non-Ubuntu machine, so Synaptic is not the right answer).

---

### Post by steven8 on 2007-02-28
I believe it's under System at the top toolbar, or Places.  Darn it, I'm at work.  But there should be an About Gnome, which should supply the answer.

---

### Post by STREETURCHINE on 2007-02-28
steven8 you are correct 

  system->about gnome

gives the version number

---

### Post by cairnsww on 2007-02-28
Thanks - but the Suse system I am working with does not have any Places and I can't find any About Gnome. Any ideas?

---

### Post by Quillz on 2007-02-28
When in the Terminal, the ```
--version
``` command will tell you what version you have installed for whatever software you use the command for. For example, if you type ```
mozilla-firefox --version
```, it might output that you have version 2.0.0.2. So try ```
gnome --version
```.

---

### Post by cairnsww on 2007-02-28
Yhanks - but:

gnome --version


Gets:

you're already running a session manager

Which is not helpful :(

---

### Post by sjbrun on 2007-02-28
To get gnome version number type
```
gdm --version
```
into the terminal.

---

### Post by Bachstelze on 2007-02-28
Here on - brrrrrr - Fedora, the comand to type in a terminal is

```
gnome-about
```

---

