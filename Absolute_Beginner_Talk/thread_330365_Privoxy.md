---
title: "Privoxy"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Paul_world10 on 2007-01-03
Hi, I am a newbie for sure.  I installed Privoxy under my account not root.  Privoxy is completely working in firefox because I can load up the preferences screen.   Anyway I need help to get root on privoxy so I can go into  Defalut.Action and modify the file.  I cant modify the file now because its read only .  So can I just boot up into root somehow?  ok bye

---

### Post by MkfIbK7a on 2007-01-03
try 
gksudo privoxy

---

### Post by Paul_world10 on 2007-01-03
I try but 

paul@desktopbox:~$ gksudo privoxy
Jan 03 00:55:35 Privoxy(b7dd76c0) Fatal error: can't check configuration file '/home/paul/config':  No such file or directory
paul@desktopbox:~$

Privoxy is located under  home folder / filesystem/etc/privoxy

thanks for your reply

---

### Post by MkfIbK7a on 2007-01-03
you say it runs in firefox
try
 gksudo firefox
if it runs from firefox this should work

---

### Post by Paul_world10 on 2007-01-03
Cool stuff for a noob like me but anyway please can I ask.    How would one get a list of everything one could gksudo on there machine?   Thank you

---

### Post by MkfIbK7a on 2007-01-03
you can gksudo any graphical program that you can run from the terminal...

---

