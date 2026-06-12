---
title: "CLI indepth tutorial"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by telegramsam on 2006-09-01
Ok, so as far as I can tell, terminal commands are a language.  I don't see that they're arbritary commands, but the syntax and pattern baffle me.  I'm not a programmer or an expert by any means, but I'd like to become much more educated in how to build commands.  Is there any publication (free or otherwise) that would educate me in Linux commands?  Are they the same throughout the distros?

---

### Post by Titus A Duxass on 2006-09-01
The best thing I can think of for you is Rute.
Do a search on the forum and you will find it.

There are several command line tutorials around as well, do some searching and some reading.

---

### Post by hw-tph on 2006-09-01
Yup, [the Rute](http://rute.2038bug.com/rute.html.tar.bz2) is a good place to start if you don't have a friend you can pester with your questions (and it also makes a good complement to computer literate friends). :)

A quick few words: The command line in Linux is usually powered by the Bash (*B*ourne *A*gain *Sh*ell) shell, but there are several others - the good ol' Bourne shell, csh, the Korn shell, zsh and so on. If you're using Linux you will want to start out learning Bash since it is by far the most common. The shell is the program that interprets the commands you write, and different shells have different syntax. However, most shells are more or less similar to the Bourne shell (but csh being less similar to Bourne and more like C programming that anything else).

But yeah, the Rute is a good place to start getting to know your system. If you want to write scripts (programs) using the Bash shell syntax, there is a brilliant guide simply called [The Advanced Bash Scripting Guide](http://www.tldp.org/LDP/abs/html/index.html). I always keep a copy on my laptop for reference.


Håkan

---

### Post by catlett on 2006-09-01
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.tldp.org/LDP/GNU-Linux-Tools-Summary/html/index.html](http://www.tldp.org/LDP/GNU-Linux-Tools-Summary/html/index.html)

---

### Post by anaconda on 2006-09-01
Just wanted to mention, that there is a command called 
"alias"
which is worth knowing...

I mean what is the point in writing "ls -la|more" each time you want to have a listing of the contents of a directory?

Many people have made a few aliases for the most common commands, so that eg. they can write "ll" instead of "ls -la|more"  or "md" instead of "mkdir" or "cd.." instead of "cd .." etc...

Oh, and yes the commands are the same in all linux & unix distributions. (there can be some small differences. eg. some commands are not available in some distributions)

---

