---
title: "Gvim config"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by jus71n742 on 2008-04-02
I am fairly new to programming and I really like using Vim in my C++ class. So when I put Ubuntu on my laptop I came across GVim I added it and I can not seem to get the syntax highlighting like that I see on the machines in the schools computer lab. Any suggestions on getting that working correctly?

---

### Post by cardinals_fan on 2008-04-02
You definitely need to edit the .gvimrc file in your home directory, but I'm not sure what you need to put in there.

---

### Post by jus71n742 on 2008-04-02
how do I get into this .gvmrc?

---

### Post by Windy_Red_Sea on 2008-04-02
to get syntax highlighting in gvim add the following line to your .gvimrc file:

syntax on

to edit the file open a terminal and type:
gedit ~/.gvimrc

Regards,
Frank

---

### Post by jus71n742 on 2008-04-03
ok I have the gedit ~/.gvimrc going and it brings up the file in text editor and nothing is in the file.  is this normal?

---

### Post by Windy_Red_Sea on 2008-04-03
Yes, it is. It just means you haven't set any preferences yet.

---

