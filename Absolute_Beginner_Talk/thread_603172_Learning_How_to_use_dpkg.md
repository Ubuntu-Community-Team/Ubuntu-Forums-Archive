---
title: "Learning How to use dpkg"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by LobbyDizzle on 2007-11-04
I am basically trying to install BitPim for my cell phone and was also having problems getting my wireless to work once I reached the install phase of it. 

I downloaded BitPim and saved it to my desktop. Following the directions on the website I found, here is what came up.

jared@jared-laptop:~$ sudo dpkg -i --force-architecture bitpim-version.deb
dpkg: error processing bitpim-version.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bitpim-version.deb
jared@jared-laptop:~$ sudo dpkg -bitpim-<tab>
bash: syntax error near unexpected token `newline'

I even tried to change the filename to bitpim-version.deb

---

### Post by Maestro23 on 2007-11-04
Make sure you are in your Desktop:

> cd ~/Desktop

*Everything in Linux is Case Sensitive.

---

