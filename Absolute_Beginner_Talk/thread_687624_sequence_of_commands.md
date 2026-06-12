---
title: "sequence of commands"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Bluedoorman on 2008-02-04
hi , I am a beginner with Linux.
In the terminal screen you can put in command lines.
Can you put these lines in a script or something that you can run ?
Can you put a shortcut on the desktop to that script ?

Thanks.

---

### Post by spiderbatdad on 2008-02-04
check out this tutorial on Bash scripts:[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
or you may find another one online. They will tell you how to create, where to store, and how to run command line programs. 
You will write your scripts using the text editor and store them in your home directory, generally.

---

### Post by bump_ on 2008-02-04
Yes both are possible.

Here is how to make scripts

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
(Note: eben though it says "advanced bash scripting" it really stats at the beginning)

To make a shortcut to the desktop for anything, just right-click on the desktop, click "create launcher" and fill in the info. It should work for scripts too.

---

### Post by frankos44 on 2008-02-04
You can place any command into a "shell script", each command is placed on a new line. A shell script is a simple text file with execute permissions enabled and can be created using any text editor of your choice such as gedit for example.

You will need to learn the shell commands and familiarise yourself with the huge number of commands available and conditional expressions etc.

There are many books on the subject. I started with  "Linux Pocket Guide". I suggest at this stage you don't use "su" command until you are familiar with how things work, it dosent take prisoners.  Try typing this at the terminal:

$ gedit abc

add the line:

echo Hello world

then save and exit

Then set the permissions for execute:

$ chmod 766 abc

To run the script type:

$ ./abc

---

