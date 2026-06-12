---
title: "Sudo"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Durden10 on 2007-07-03
Hi, I am completely new, have just installed ubuntu a couple of days ago.

I have one question to which I couldnt find an answer (or didnt look properly),
how can you remain root-user, or sudo, during a session in the linux-explorer? I have a bunch of files edited in my personal directory and have to copy them back and forth to a "secured" directory, doing this through the terminal is time-consuming...
Thanks and best regards,
Durden

---

### Post by meborc on 2007-07-03
what file manager do you use? nautilus (gnome)?

just start the file manager like this ```
gksudo nautilus
```
that way you will have the root privileges in the file manager (change the nautilus in the command to the name of your manager, eg thunar...)

---

### Post by Durden10 on 2007-07-03
Well.... I dont know the exact name of the browser, its the standard that comes with the original installation....
Durden

---

### Post by Malibu Illusion on 2007-07-03
You can use the command given to you by meborc to start a copy of Nautilus as a root user to allow you to copy/edit things in those directories.  Are you sure this wouldn't be quicker in a CLI though?  If all the files share a common extension, you could perform a:

```
sudo cp *.bin /usr/whatever/dir
```

For example to copy multiple files across at the same time.

---

### Post by meborc on 2007-07-03
if you are running gnome (ubuntu) then it is nautilus, if you are running xfce (xubuntu) it is thunar and in kde (kubuntu) it should be konqueror

---

### Post by Durden10 on 2007-07-03
Problem solved, thanks for the quick reply!

---

