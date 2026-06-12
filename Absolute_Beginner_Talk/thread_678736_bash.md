---
title: "bash"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-26
can someone explain to me what the command bash represents?  i'm just looking for an understanding of what it does and an example of it's usage if possible.  thanks.

---

### Post by Paul820 on 2008-01-26
Bash isn't a command it's a shell [http://en.wikipedia.org/wiki/Bash]("http://en.wikipedia.org/wiki/Bash")

---

### Post by mali2297 on 2008-01-26
If you explicitly see a command **bash**, I would guess that it is used to execute a shell script.
```

bash yourscript.sh

```
For more information about writing scripts, see for example
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by mikeyphi on 2008-01-26
> **Matt26 said:**
> can someone explain to me what the command bash represents?  i'm just looking for an understanding of what it does and an example of it's usage if possible.  thanks.

Open a terminal and enter:
man bash

for an explanation of the format

---

### Post by Matt26 on 2008-01-26
thanks- as an example, what would the command sudo bash do?

---

### Post by Faud on 2008-01-26
You wouldn't type sudo bash
read
[http://en.wikipedia.org/wiki/Bash](http://en.wikipedia.org/wiki/Bash)
and example of a script would be like a conky start up script

---

### Post by mikeyphi on 2008-01-26
> **Matt26 said:**
> thanks- as an example, what would the command sudo bash do?

Refer to my previous post for the correct use of the shell.....(sudo bash does nothing in itself)
however, as mentioned in another post, bash followed by ascript.sh (i.e. some set of commands) will execute that set of commands.

---

### Post by Christmas on 2008-01-26
Bash is a command line interpreter, that is you type commands in a terminal-like program (GNOME Terminal, Konsole) and Bash interprets them and gives you output. It is also called a 'shell'. Others would be csh (C Shell), ksh (Korn Shell).
You can read [here](http://www.tuxfiles.org/) and [here](http://linuxcommand.org/) and I'd also recommend the book O'Reilly Learning the UNIX Operating System.

---

