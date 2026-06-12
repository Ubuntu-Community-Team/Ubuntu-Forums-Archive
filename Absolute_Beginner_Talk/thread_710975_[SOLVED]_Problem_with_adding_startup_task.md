---
title: "[SOLVED] Problem with adding startup task"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by jualansandal on 2008-02-29
Hi all, I would like to ask about adding task.
The task is to load a script from specific folder in home with parameter, for example the script name is carte.sh and it has two parameter to run ( ip and port).
my question is what is the best way to add it into my startup task ?
If I it is already added to startup then does the console will shown up at startup ?

thanks all

---

### Post by kpkeerthi on 2008-02-29
Assuming the script is capable of reading parameters from the input, you would need to add
```

/home/<user>/path/to/script/carte.sh xxx.xxx.xxx.xxxx pppp

```
under Command in System -> Preference -> Session.

xxx.xxx.xxx.xxxx => Actual IP you want to pass
pppp => Port Number

Also make sure the script is executable
```
chmod u+x /path/to/script/carte.sh
```

EDIT: the console won't show up when you add to System -> Preference -> Session

---

### Post by paulmilliken on 2008-02-29
If you want a program to start when you log in then under the "System" menu go to "preferences" then "sessions".  Then click "add" and enter the command that you would like to run just like you would if you were to run it from a terminal.

Edit:  Someone beat me to it - see post above for a more detailed explanation...

---

### Post by jualansandal on 2008-02-29
thanks, It is working , but do you know how to show the process from terminal , because the script task is loading a server(Carte) and I would like to see the running tasks.

---

### Post by kpkeerthi on 2008-02-29
Change the 'Command' to
```

gnome-terminal -e /home/<user>/path/to/script/carte.sh xxx.xxx.xxx.xxxx pppp

```

---

### Post by jualansandal on 2008-03-02
ok, thanks

---

