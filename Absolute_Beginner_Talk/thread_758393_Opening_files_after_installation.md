---
title: "Opening files: after installation"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Wantingtolearn on 2008-04-18
i have used both synaptic and command prompt to install a variety of programs, but importantly G++.  When I go to usr/bin to click them they won't open.  What am i doing wrong.  Please help, and a little thank you in advance.  i am using Ubuntu 8.04 beta.

---

### Post by Tatty on 2008-04-18
try running them from the command line, im pretty sure g++ doesnt have a gui.  Go to a terminal and type g++.

if you need help try "g++ --help"  for a brief useage guide  or try "man g++" for the g++ manual.

---

### Post by Wantingtolearn on 2008-04-18
Thank you for answering, this is what I am getting.

kmichaellong@kmichaellong-laptop:~$ G++
bash: G++: command not found
kmichaellong@kmichaellong-laptop:~$ /.G++
bash: /.G++: No such file or directory
kmichaellong@kmichaellong-laptop:~$ gksudo G++
sudo: 1 incorrect password attempt
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSkmichaellong@kmichaellong-laptop:~$ .\G++
bash: .G++: command not found
kmichaellong@kmichaellong-laptop:~$ /.G++
bash: /.G++: No such file or directory
kmichaellong@kmichaellong-laptop:~$ gksudo G++
kmichaellong@kmichaellong-laptop:~$ g++
g++: no input files
kmichaellong@kmichaellong-laptop:~$ /.g++
bash: /.g++: No such file or directory
kmichaellong@kmichaellong-laptop:~$ 


I hope this helps, and helps me thanks.

---

### Post by ramjet_1953 on 2008-04-18
Don't forget that commands are case sensitive.

shouldn't you be typing g++

NOT G++

Regards,
Roger :cool:

---

### Post by Wantingtolearn on 2008-04-18
yeah, I realized that and in the later part I changed it to g++, was that the right command for executing the program "/."

---

### Post by ad_267 on 2008-04-18
Please don't double post: [http://ubuntuforums.org/showthread.php?t=758319](http://ubuntuforums.org/showthread.php?t=758319)

---

### Post by Tatty on 2008-04-18
the command "g++" will execute the program.  You need to provide it with parameters to tell it what to do though, i assume the main one will be the file you are trying to compile - although i have never used it before myself.

read the help and manual for more info.

---

