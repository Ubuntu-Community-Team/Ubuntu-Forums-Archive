---
title: "close xserver"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by jijin on 2007-07-24
I am trying to install the nvidia drivers but can't figure out how to drop to command line. I have done init 6 and ubuntu reboots. I have used ctrl-alt-f1 and nvidia drivers say I still haven't closed xserver...

How do I do this. I would use envy to install it but it's not detecting my card geforce 7025

any help?

EDIT: resricted drivers thingy doesn't help either... it tells me I don't needs them :(

---

### Post by Mornedhel on 2007-07-24
To kill a running X server : Ctrl Alt Backspace

---

### Post by jijin on 2007-07-24
> **Mornedhel said:**
> To kill a running X server : Ctrl Alt Backspace

all that does is restart it. it does not drop to anything interactive which is what I need.

sorry I should have mentioned that I have done that too

---

### Post by atomicthumbs on 2007-07-24
runlevel 2?

"sudo init 2"

EDIT: Whoops. try 1.

"sudo init 1"

that'll put you in single-user mode.

---

### Post by jijin on 2007-07-24
> **atomicthumbs said:**
> runlevel 2?

"sudo init 2"


```
jijin@ubuntu:~$ sudo init 2
Password:
jijin@ubuntu:~$ sudo init 2
jijin@ubuntu:~$

```

is what I get... else it does nothing

thanks again for people's help

---

### Post by Malibu Illusion on 2007-07-24
```
sudo /etc/init.d/gdm stop
```

Is what you're looking for. (kdm for KDE)

---

### Post by jijin on 2007-07-24
> **Malibu Illusion said:**
> ```
sudo /etc/init.d/gdm stop
```

Is what you're looking for. (kdm for KDE)

Thanks, but when I did that it dropped to a not useable command line _like_ interface

I could enter in things but they would not take.. It's like typing into a text editor

---

### Post by Malibu Illusion on 2007-07-24
Go ahead and hit ctrl+alt+f1 after doing so.  

In fact, why not drop back to the CLI and stop the window manager from there.  Ctrl+alt+f1 then issue the stop command.  You should then be able to install the drivers.

---

### Post by Dedoimedo on 2007-07-24
Hello,
Try as suggested /etc/init.d/gdm stop for gnome, kdm stop for kde ...
Then, try Ctrl + Alt + F1-6. One of them should work.
Dedoimedo

---

### Post by Aeonoris on 2008-03-14
I had the same problem, found this thread and got the driver installed, but now I can't figure out how to get back to my GUI...

Ctrl-alt-F7 doesn't do anything, and I can't init 7 or anything...  Ctrl-alt-backspace seems to make me unable to type anything (but stay in the command prompt), regardless of which runlevel I'm on...

Any help?

---

### Post by Aeonoris on 2008-03-14
Nevermind, I got it working, though now "GLX" isn't working...  But that's for a different thread :D

---

