---
title: "help how to"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by moondoggy17 on 2007-11-29
ok i'm try yo install an awn dock with awn curves. i'm using the guide on this page 
[http://ubuntuforums.org/showthread.php?p=3506749&page=11]("http://ubuntuforums.org/showthread.php?p=3506749&page=11")
and when i try to change sources.list i get a msg saying You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
so what i need is to get around this

---

### Post by overdrank on 2007-11-29
> **moondoggy17 said:**
> ok i'm try yo install an awn dock with awn curves. i'm using the guide on this page 
[http://ubuntuforums.org/showthread.php?p=3506749&page=11]("http://ubuntuforums.org/showthread.php?p=3506749&page=11")
and when i try to change sources.list i get a msg saying You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
so what i need is to get around this

Hi and did you use this command ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by kellemes on 2007-11-29
I assume you mean **gksudo "gedit /etc/apt/sources.list"** ? This gives you the message?
Don't forget the gksudo.. this gives you root-privileges..

---

### Post by edwardTheGreat on 2007-11-29
backup the file first
```
 sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```
open the sources.list using 
```
gksudo gedit /etc/apt/sources.list 
```

---

### Post by limac on 2007-11-29
just type in sudo gedit /etc/apt/sources.list in the run box (Alt+F2).

---

### Post by limac on 2007-11-29
on second thought type that in the terminal.

---

### Post by eldepeche on 2007-11-29
You should try to use more descriptive thread titles. "what is" and "help how to" don't give anyone any idea what you're posting about. If you included more information, you might get more responses. Try "What is AWN?" or "How to install AWN dock?"

---

