---
title: "Is the &quot;shell&quot; the same thing as the &quot;terminal&quot;?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-07-04
Is the "shell" the same thing as the "terminal"?
I'm trying to install PEAR on my Desktop LAMP by following these instructions.
[http://www.sitepoint.com/article/getting-started-with-pear/2](http://www.sitepoint.com/article/getting-started-with-pear/2)
But I get this instead.
```
mike@sanka:~$ **php -v**
bash: php: command not found
mike@sanka:~$
```

---

### Post by Majorix on 2007-07-04
```
sudo apt-get install php5-cli
```

That will install php client, which you can query with arguments like -v.

---

### Post by jingo811 on 2007-07-04
Huh huh it worked \\:D/ tnx!

```
mike@sanka:~$ **php -v**
PHP 5.1.2 (cli) (built: May 22 2007 20:23:21)
Copyright (c) 1997-2006 The PHP Group
Zend Engine v2.1.0, Copyright (c) 1998-2006 Zend Technologies
mike@sanka:~$

```

---

### Post by hartz on 2007-07-06
> **jingo811 said:**
> Is the "shell" the same thing as the "terminal"?


Yes, for all practical purposes, it is.  When you are instructed to "enter commands into" a terminal or shell or console, these things are equivalent.

If you want to get technical, they are different.  The shell is the command interpreter which typically runs inside a terminal or console.

A terminal can be an X-Windows program which presents a window running a shell.  It can also be a terminal session connected to a text-mode login - such as the ones you get  when you press CTRL-ALT-F1.  It can also be a remote login program via a network, or a device connected via a serial port.  I would go so far as to say that the terminal is somewhat of a concept, but purists would disagree.  **All terminals have in common that they are the connection points for shell input and output**, and are represented by "terminal devices" in the /dev directory.  Examples are /dev/tty1

The console is a special terminal - A computer can have many terminals, but only one console.  The console is the first terminal which is made active, and it is the default device onto which alert and panic messages are displayed on, and also where bootup/shutdown messages are shown.

---

### Post by swoll1980 on 2007-07-06
The Terminal is the middle man between you and the shell. give you some features like copy and paste customizable colors, text, stuff like that

---

