---
title: "adding printer"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by shantz24 on 2007-03-28
I am attempting to add my Lexmark Z605 printer so i can use it.  I am following these instructions, [https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605), but i cant figure it out.  I have downloaded the driver to my desktop, should i put it somewhere else?  i also installed alien and the libstdc++5.  however where is says to run the following commands, is each line a command?  i am new to ubuntu and still shaky on the whole command thing.  how should i go about running those commands?

UPDATE:  resolved using [http://www.ubuntuforums.org/showthread.php?t=83456&highlight=z605](http://www.ubuntuforums.org/showthread.php?t=83456&highlight=z605).  followed these scripts then i just added a printer and used the installed driver and it worked.

---

### Post by halitech on 2007-03-28
looks like each line is a command but stop where the # is in each line

so you would open a terminal, then copy and paste each command in after changing to the Desktop (caps are important in Linux) and hit enter

ie, 
```
cd ~/Desktop
```

```

then paste tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz

```

etc

---

### Post by shantz24 on 2007-03-29
when i run "tail -n +143 z600cups-1.0-1.gz.sh" it goes crazy.  Terminal begins to fill up with letters and symbols and starts beeping.  that cant be good.

---

### Post by shantz24 on 2007-03-29
any ideas?

---

### Post by halitech on 2007-03-29
are you using 6.10 or 7.04 or 6.06 or below?

---

### Post by shantz24 on 2007-03-29
sorry should have added this before. 6.10

ok, i tried again this morning and got passed the previous problem.  i was not thinking and did not copy the entire command.  however when i try to run "dpkg -i *.deb" terminal says i need superuser privileges.  i am the only user on this, is there someway to obtain these privileges?

---

