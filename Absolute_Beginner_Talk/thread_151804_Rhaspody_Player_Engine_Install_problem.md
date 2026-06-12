---
title: "Rhaspody Player Engine Install problem"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by The Running Board on 2006-03-28
Ok...so Im relatively new to Linux...but getting the hang of it rather quickly...but I keep trying to use the Rhapsody.com player...and for some reason it keeps failing the insall, saying that I am out of space...which doesnt make any sense because I have 9.5 GB free...anyone have a clue whats wrong?

---

### Post by nacs on 2006-11-21
I was having the same problem trying to install and just found the answer after a bit of Googling around so here it is in case someone searches the Ubuntu forums:

The easy fix is to create the directory .mozilla/plugins/ in your home directory (fire up the console and type in **mkdir -p ~/.mozilla/plugins** ).

Apparently the plugin tries to install itself in that directory and gives that inaccurate "Out of space" error if that folder doesn't exist.

---

