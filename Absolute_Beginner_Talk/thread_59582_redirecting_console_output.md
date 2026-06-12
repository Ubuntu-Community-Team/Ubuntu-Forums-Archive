---
title: "redirecting console output"
date: 2005-08-24
forum: Absolute Beginner Talk
---

### Post by red_Marvin on 2005-08-24
When I run a certain program, it often freezes the computer so I have to do a cold reboot.
Since I'm running the program from console it is possible that eventual error messages
is printed there but get lost at the 'boot.
To solve this it it would be nice to have the console not only printing to the window
but also a log file of some sort.
Is this possible at all? Easy? How? ... [yada yada I'm a linux noob :wink: ]

---

### Post by vruum on 2005-08-24
something like this would work: 

"command" >> "log_file"

where command is the program name and log_file is the name of the logfile

---

### Post by red_Marvin on 2005-08-24
Thanks, I'll try it out...  :)

---

### Post by macgyver2 on 2005-08-24
[QUOTE=vruum]something like this would work: 

"command" >> "log_file"

where command is the program name and log_file is the name of the logfile[/QUOTE]
That's only gonna send the output to the file--which I do realize in this case is probably the only place it needs to go, with the computer locking up and all that...
[QUOTE=red_Marvin]To solve this it it would be nice to have the console not only printing to the window but also a log file of some sort.[/QUOTE]
However, if you really want the output to go to both the screen and the file, take a look at the [tee]("http://www.linux.org/lessons/beginner/l10/lesson10b.html") command.

---

### Post by cwaldbieser on 2005-08-24
[QUOTE=red_Marvin]Thanks, I'll try it out...  :)[/QUOTE]
If you want the errors as well as the output:
```
$ command > logfile 2>&1
```

---

### Post by red_Marvin on 2005-08-25
I'll see if it makes any difference, the logs have been empty sofar...

---

