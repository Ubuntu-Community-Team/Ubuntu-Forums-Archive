---
title: "find a file/dir"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by natman on 2007-08-13
Hello this in no doutb a  truly silly question but i am trying to learn a little bit of terminal stuff from here
[HTML]http://www.linuxcommand.org/wss0020.php[/HTML]
Just wanted to know where is the ./bash_profile directory located? i cant seem to find it in /hom/user i  am using KDE
Is it safe to add[HTML]alias l='ls -l'[/HTML] to it?

---

### Post by schorsch on 2007-08-13
It is not a directory but a plain file called ".bash_profile". The . at the beginning means that it is a hiden file so to see it in konqueror you have to enable the hidden file view:

View --> Show Hidden Files

To see it in a terminal session type "ls -a"

And yes, it is safe to add the code although most people I know use ll instead of l as the alias name.

---

### Post by xadder on 2007-08-13
You want the file .bash_profile, not ./bash_profile. There is a big difference, in that
the dot is part of the filename in the first version, but in the 2nd the filename is just bash_profile, located in the current directory, which is signified by "." in unix-like systems. 

So, just go to your home directory and edit the file:

cd
vi .bash_profile

(or nano or gedit or xxxx nstead of vi).

Note that files beginning with a dot are invisible to a standard "ls" command. Use "ls -a" to see them - there are usually many in the home directory.

Actually, I tend to put such things in my .bashrc file instead. This is also advised further down in the web-page you were looking at.

Good luck with the command-line learning. It is well worth the effort!

---

### Post by Hospadar on 2007-08-13
Just for learning purposes, since everyone likes to learn =)
the ./ is used to execute local executables that are not in the PATH environment variable.  so if you had an executable "foo" in the directory you are in, and that directory is not in the PATH, you would run a ./foo to run that executable.

---

