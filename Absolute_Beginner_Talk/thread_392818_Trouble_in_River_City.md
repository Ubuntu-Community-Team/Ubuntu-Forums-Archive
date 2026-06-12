---
title: "Trouble in River City"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-25
sudo gedit /etc/apt/sources.lst

Now you see it, now you don't. I type the above command in Terminal and get the menu list. I edit it and reboot. Now I go back and type the same command and voila: da nada, kaput, nothing. Just a blank Menul,list.

What's up with this? Anyone know how to fixum?

kh :confused:

---

### Post by taurus on 2007-03-25
If you use gedit editor, you need to use **gksudo** instead of sudo.

What's the output of this command from a terminal?

```
ls -la /etc/apt
```

---

### Post by kittyhawk63 on 2007-03-25
> **taurus said:**
> If you use gedit editor, you need to use **gksudo** instead of sudo.
What's the output of this command from a terminal?
```
ls -la /etc/apt
```

kittyhawk63@kittyhawk63:~$ ls -la /etc/apt
total 40
drwxr-xr-x   4 root root 4096 2007-03-24 21:16 .
drwxr-xr-x 108 root root 4096 2007-03-24 21:19 ..
-rw-r--r--   1 root root   30 2007-03-24 08:49 apt.conf
drwxr-xr-x   2 root root 4096 2007-03-24 19:46 apt.conf.d
-rw-------   1 root root    0 2006-08-05 16:20 secring.gpg
-rw-r--r--   1 root root 1772 2007-03-24 21:16 sources.list
-rw-r--r--   1 root root 1784 2007-03-24 08:55 sources.list~
drwxr-xr-x   2 root root 4096 2006-04-18 12:47 sources.list.d
-rw-------   1 root root 1200 2006-08-05 16:20 trustdb.gpg
-rw-r--r--   1 root root 2393 2006-08-05 16:20 trusted.gpg
-rw-r--r--   1 root root 2381 2006-08-05 16:20 trusted.gpg~
kittyhawk63@kittyhawk63:~$

---

### Post by taurus on 2007-03-25
Well, there it is.

```

**-rw-r--r-- 1 root root 1772 2007-03-24 21:16 sources.list**

```

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by kittyhawk63 on 2007-03-25
> **taurus said:**
> Well, there it is.

```

**-rw-r--r-- 1 root root 1772 2007-03-24 21:16 sources.list**

``````
gksudo gedit /etc/apt/sources.list
```

Ok! What is "There it is"? What exactly do you see Taurus? I am giving it the fix as you respond to my inquiry. Thanks again. Are you looking over my shoulder? You seem to be right there when I experience another "what now?"

---

### Post by kittyhawk63 on 2007-03-25
> **kittyhawk63 said:**
> Ok! What is "There it is"? What exactly do you see Taurus? I am giving it the fix as you respond to my inquiry. Thanks again. Are you looking over my shoulder? You seem to be right there when I experience another "what now?"

It did show up again. What did you tell it that made it behave? what is the difference between sudo and gksudo?

---

### Post by taurus on 2007-03-25
I just closed my eyes and clapped my hands twice...

Or maybe because I lived in Northern California before!

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by kittyhawk63 on 2007-03-25
> **taurus said:**
> I just closed my eyes and clapped my hands twice...
Or maybe because I lived in Northern California before!
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

lol
Is there a site that I can learn the basic sudo, gksudo commands and what they do? I would like to learn them. Thank you again for your invaluable help.
kh

---

### Post by taurus on 2007-03-25
You can read the manpage about every command from a terminal.  Just type

```
man sudo
man gksudo
-or-
man **command**
```

---

### Post by kittyhawk63 on 2007-03-25
> **taurus said:**
> You can read the manpage about every command from a terminal.  Just type
```
man sudo
man gksudo
-or-
man **command**
```

Thank you Taurus. I will do that.
kh

---

