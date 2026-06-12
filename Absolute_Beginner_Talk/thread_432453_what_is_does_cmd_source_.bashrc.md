---
title: "what is does cmd source .bashrc ?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by gotquestions on 2007-05-04
so i saw a friend typed on cmd line:

$>source .bashrc 

i heard that it updates something
i typed: man source and nothing could be found. what is it?

---

### Post by YoG%*@ on 2007-05-04
hi there, 

[http://unix.t-a-y-l-o-r.com/UAsource.html]("http://unix.t-a-y-l-o-r.com/UAsource.html")
in short: it sends the contents of a text file to the shell.

hth
mux

---

### Post by Stephen Howard on 2007-05-04
'Source' isn't an OS command, but a builtin command inside bash.  To find out about bash builtins, type 'help xxx' where xxx is the command (ie 'help source').

---

