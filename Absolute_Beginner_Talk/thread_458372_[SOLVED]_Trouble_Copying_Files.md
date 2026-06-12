---
title: "[SOLVED] Trouble Copying Files"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by 42Wired on 2007-05-29
Every time I try to copy something to a different directory, I get the message ```
cp: omitting directory '[source directory]'
``` whether I type [FONT="Courier New"]sudo[/FONT] or not.

I know how to copy files, but all of the sudden it isn't working. What am I doing wrong?

---

### Post by Inxsible on 2007-05-29
Try this:
```
 sudo cp -r  /entire path to location /entire path to new location
```
 
eg```
 sudo cp -r /home/Desktop/Screenshot.png /shared/mydrive/tmp/Screenshot.png
```

---

### Post by jasonlfunk on 2007-05-29
> **42Wired said:**
> Every time I try to copy something to a different directory, I get the message ```
cp: omitting directory '[source directory]'
``` whether I type [FONT="Courier New"]sudo[/FONT] or not.

I know how to copy files, but all of the sudden it isn't working. What am I doing wrong?

that is telling you that it isn't going to copy the directory. If you want to do a recursive copy, add a -r. 

```
 cp -r [source] [dest] 
```

---

### Post by 42Wired on 2007-05-29
That did it. Thanks.

What does recursive copy mean, and why haven't I encountered it before?

---

### Post by Inxsible on 2007-05-29
Go to a terminal and type in
 
```
man cp
```
 
That will give you more information on the command and its parameters. Its true for any command that you want to know abt.
It stands for manual for the command :)
i.e. ```
 man commandname
```

---

### Post by Henry Rayker on 2007-05-29
recursive copying will copy the directory and all of its contents (and if it contains a directory, all of that directory's contents etc. etc.)

---

### Post by 42Wired on 2007-05-29
Oh, instead of copying a single file. Thanks.

---

