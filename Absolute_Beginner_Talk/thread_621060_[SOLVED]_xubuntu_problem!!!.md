---
title: "[SOLVED] xubuntu problem!!!"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-11-23
ok the taskbar's in xubuntu are missing on one of the accounts...and i dont rely know whats going on :confused:

help please!

---

### Post by hyper_ch on 2007-11-23
Currently I don't recall what the according package is called.

Login with a user that works and run in the shell this command and post the output here:

```

ps aux | grep xfce4

```

It's something with xfc4-panel......... anyway, the output of the command above will tell.
If you find out yourself which one it is, then login to the "defunct" account, open a terminal (Alt + F1) and run
```

xfce4-panel.... &

```
Just enter the correct name there, that will start the panels again. The " &" at the end mean, that the program shall go on running even if the terminal is closed. Once you have the panels back, logout of Xubuntu BUT SAVE THE SESSION.

Next time it will be there again.

---

### Post by vambo on 2007-11-23
If you mean the xfce panels then this might help
[http://ubuntuforums.org/showthread.php?t=608389]("http://ubuntuforums.org/showthread.php?t=608389")

---

### Post by kamitsukai on 2007-11-23
how do i get it to sasve the last session?

---

### Post by hyper_ch on 2007-11-23
Upon the logut dialog box.

---

