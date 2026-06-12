---
title: "noob question"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by TheRingmaster on 2006-04-14
what are some _basic_ commands that i should know before trying to tackle the terminal? :-k  I tried searching for it but couldn't find any posts about it.

---

### Post by jimrz on 2006-04-14
Welcome,

   [[COLOR="Sienna"]**_Here's_**[/COLOR]]("http://www.ss64.com/bash/") a good place to start

---

### Post by andlinux21 on 2006-04-14
you did a google on linux commands and didnt come up with anything?
well i am pretty much a n00b but I can figure things out with the help of the forums. You may want to get a linux book to kind of help you along your way.:D

---

### Post by confused57 on 2006-04-14
Here's an excellent tutorial poste by Kyral:

[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)

or another one you may want to read over:

[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)

---

### Post by Mustard on 2006-04-14
[http://ubuntuforums.org/showthread.php?t=45651](http://ubuntuforums.org/showthread.php?t=45651)
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Some more just to make it complex as to which ones to choose. ;)

---

### Post by IYY on 2006-04-14
Well, here are the most basic commands, that you need to navigate through the terminal and such:

```
ls: prints out the contents of the current directory
pwd :prints out the current directory
cd <dir name>: go to the directory specified
.: a shortcut for the present directory
..: a shortcut for the parent directory
(for example, if you want to execute a command in the current directory, you use ./commandname)
mv <source> <destination>: move the file source to the directory destination
cp <source> <destination>: similar to move, but to copy the file
rm <file>: removes a file. 
rm -r <directory>: removes a directory and all its contents.
less <text file>: read a long text file, scrolling with the arrow keys
cat <text file>: print out a short text file on the screen
echo <text>: prints out everything after the echo command
nano <filename>: edit a file
grep <text> <file>: search for the specified text in the specified file (if a file is not specified, it searches in the standard input)
top: shows the processes that take up most cpu/memory
ps aux: shows all processes
killall <program name>: stop running a program
cal: display a calendar
date: display time/date
```

And the most important command: man <command>. It gives you the manual page for the specified command.

Here's how to use pipes and redirects:

command1 > filename

will print the output of command1 to the specified file rather than the screen.

command1 >> filename

will do the same as the above, but will append instead of overwriting

command1 | command2

the output of command1 will be the input of command2. For example 
**ps aux | grep gaim** will search for "gaim" in the currently running processes.

---

