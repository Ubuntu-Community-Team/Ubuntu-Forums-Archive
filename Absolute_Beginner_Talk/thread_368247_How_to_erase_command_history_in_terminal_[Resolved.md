---
title: "How to erase command history in terminal? [Resolved]"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by humbll on 2007-02-23
When I open a terminal window and press the up arrow, it shows the last command I typed, pressing again it shows the second to last command, and so on. How do I erase these previous commands from the memory of the terminal?

---

### Post by aysiu on 2007-02-23
Try this: ```
ln -s ~/.bash_history /dev/null
```

---

### Post by yabbadabbadont on 2007-02-23
Add:

export LESSHISTFILE="-"
unset HISTFILE

To your ~/.bashrc file.  That will stop the creation of both bash and less history files.

---

### Post by humbll on 2007-02-23
I don't want to stop the commands from ever being stored in history, it is useful, but at times I may want to erase them manually, is there a command to type that will let me do that?

---

### Post by shoaibi on 2007-02-23
as soon as you open terminal type
```

 histrory -c

```

or
```

echo "" > ~/.bash_history

```

this will clean all PREVIOUS commands

---

### Post by xyz on 2007-02-23
```
history -c
```
(typo)

---

### Post by yabbadabbadont on 2007-02-23
> **xyz said:**
> ```
history -c
```
(typo)

Could this be considered a case of "revisionist history"?   :lol:

---

### Post by xyz on 2007-02-23
Sometimes I like to "see" all command lines in one txt file.
I open /home/user/.bash_history...and you can erase the commands you don't want.
Also good for non-command-line afficionados.

---

### Post by xyz on 2007-02-23
> **yabbadabbadont said:**
> Could this be considered a case of "revisionist history"?   :lol:

LOL!!

---

### Post by shoaibi on 2007-02-23
sorry it was 
```

history -c

```

---

### Post by humbll on 2007-02-23
awsome, thanks everyone!

---

