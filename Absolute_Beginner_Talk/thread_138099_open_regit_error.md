---
title: "open regit error"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-01
everytime fromcommand line I open redit I get

(gedit:11041): Gtk-WARNING **: cannot open display:


what have I failed to install?

lex;)

---

### Post by Pragmatist on 2006-03-01
What happens if you try: ```
sudo gedit
```??

---

### Post by lex1 on 2006-03-01
that works fine 

sudo gedit

but when for example

I do

sudo gedit /var/log/messages

or some other comand I get the error message as in my first post.

lex:(

---

### Post by %hMa@?b&lt;C on 2006-03-01
sudo killall gdm 

sudo gdm

sudo gedit

see if that works

---

