---
title: "Equivalent of Program Files in linux"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2007-11-11
Hello I was just wondering where are programs installed by default like in windows it is always C:/Program Files/program name so what is this in Ubuntu (7.10).

PS I want to know this so I can add programs for startup but I want to be able to do it from the Terminal instead of Sessions. I know 1 command - sudo nano /etc/modules - but when I put Skype in the list nothing changed. What have I done wrong?

---

### Post by dward526 on 2007-11-11
Programs are usually installed in /bin or /sbin  

About your skype, sorry I cant help.

---

### Post by ViRMiN on 2007-11-11
Skype will be /usr/bin/skype :)

---

### Post by sailor2001 on 2007-11-11
you could right click your program and add to panel or you could get katapult so you only have to type 1 or 2 letters

---

### Post by mcduck on 2007-11-11
There isn't exact equivalent of the 'Program Files'-directory in Linux. Instead of putting all files of a program into one single directory Linux puts all files of same type from all your programs in one place. So your programs are spread all around the file system, executable files in /usr/bin, documents in /usr/share/doc, icons in /usr/share/icons or /usr/share/pixmaps and so on. Programs may also have their own directory in /usr/share.

Anyway, for launchers the only thing you need is the executable, and that you will find from /usr/bin.

Usefull commads for finding out where your program are installed are 'which' and 'whereis'. 'which' will tell you where the executable file for the program is, for example 'which firefox' would respond '/usr/bin/firefox'. And 'whereis' will list you all locations where the program has it's files installed.

---

### Post by evilregis on 2007-11-11
Are you typing 'skype' or 'Skype' in your list?  It should run if you type 'skype'.  Remember Linux is case-sensitive.

---

