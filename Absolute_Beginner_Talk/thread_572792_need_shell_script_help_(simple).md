---
title: "need shell script help (simple)"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by totalnub on 2007-10-10
hey guys i need to make a shell script for a class of mine. here are the requirements:
 
 make a script called lslw, that is executed as ./lslw op, where op is either -w or -l. if op is -l, then the script should output the names of all the files in the current directory sorted in increasing order of the number of lines in the files. if op is -w, then it should output the names of all the files in the directory sorted in increasing order of the number of words in the files.
 
 I really appreaciate the help that you guys give people

---

### Post by llamakc on 2007-10-10
man ls
man wc

Sure hope they're no binary files in that directory.

---

### Post by HermanAB on 2007-10-10
Here you go:
[http://www.tldp.org/HOWTO/text/Bash-Prog-Intro-HOWTO](http://www.tldp.org/HOWTO/text/Bash-Prog-Intro-HOWTO)

---

### Post by totalnub on 2007-10-10
EDIT: SOLVED!!!!

i'm dumb, but i figured it out :)
all i had to do was use the wc and sort programs.
my script looks like this:
```

#!/bin/sh
wc * $1 | sort -n

```
really simple when you know what works :)


i've got a basic understanding of shell programming, it's just that this one in particular is stumping me. should i pipe the output of ls to wc? and how do i invoke the arguments. my teacher says we shouldn't need an if statement to do this.
please help. i hate begging for help, but this assignment is due in 45 min lol.

---

### Post by kevdog on 2007-10-10
Does this really work -- I mean if you have a collection of directories and files in the current directory, you need to filter out the directories, symbolic links, etc to leave just the files behind -- on this list you can do wc.


I think to generate a list of files only it would be something like this:
ls -l | grep "^-" | awk '{print $8}'

This would filter out all the "exta crap"

---

