---
title: "GCC Command?"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by twiistedkaos on 2006-05-13
Why does the command:
```

gcc

```
Not work? I've seen gcc compile when installing deb packages... so am I missing something?

---

### Post by tonyr on 2006-05-13
**gcc** is not installed by default.  Install the package **build-essential**.

---

### Post by Sef on 2006-05-13
To build from source, you need gcc.  It is part of the build-essential package.

---

### Post by twiistedkaos on 2006-05-13
[QUOTE=tonyr]**gcc** is not installed by default.  Install the package **build-essential**.[/QUOTE]
I am new to Ubuntu and don't quite know how to use apt-get, I am use to yum >.>

---

### Post by catlett on 2006-05-13
Pretty much the same concept. Open the terminal and type ```
sudo apt-get install build-essential
``` You will be prompted for your user password. There is no su and switching to root in Ubuntu. Just put sudo before commands to execute as root.

---

### Post by twiistedkaos on 2006-05-13
[QUOTE=catlett]Pretty much the same concept. Open the terminal and type ```
sudo apt-get install build-essential
``` You will be prompted for your user password. There is no su and switching to root in Ubuntu. Just put sudo before commands to execute as root.[/QUOTE]
Alright thanks :), I did notice that you can't use su. Why not though?

---

### Post by tonyr on 2006-05-13
Long explanation somewhere else.   Basically an Ubuntu policy decision to not 
have a root user by default for security purposes.

EDIT:...or is it Debian policy?...

---

### Post by twiistedkaos on 2006-05-13
[QUOTE=tonyr]Long explanation somewhere else.   Basically an Ubuntu policy decision to not 
have a root user by default for security purposes.

EDIT:...or is it Debian policy?...[/QUOTE]
Alright, I see. I'm going to thread hi-jack my own thread for a moment, also where is the python include directory? Because I am having problems compiling a few things that require python:
```

checking for Python include path... find: /usr/include/python/: No such file or directory

```

---

### Post by Sef on 2006-05-13
To install build-essential, do this:

sudo apt-get update

sudo apt-get install build-essential


> Originally Posted by tonyr
Long explanation somewhere else. Basically an Ubuntu policy decision to not
have a root user by default for security purposes.

EDIT:...or is it Debian policy?...

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

