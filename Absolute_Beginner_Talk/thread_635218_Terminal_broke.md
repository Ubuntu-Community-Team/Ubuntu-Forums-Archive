---
title: "Terminal broke"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Neox38 on 2007-12-08
I was trying fix an issue where once you started the terminal it would say bash alias not found.  I found a command that was supposed to fix it but now all I see is the blinking cursor and no commands work.

command:

cp .profile .bashrc

---

### Post by taurus on 2007-12-08
Sounds like you've screwed up your ~/.bashrc.  Try editing it if you can by pressing <Alt>F2 and type 

```
gedit ~/.bashrc
```

---

### Post by Neox38 on 2007-12-08
I get this, though it looks normal.

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f ~/.bashrc ]; then
	. ~/.bashrc
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

---

### Post by ptn107 on 2007-12-08
A fresh .bashrc file looks as follows...

[http://paste.ubuntu-nl.org/47431/](http://paste.ubuntu-nl.org/47431/)

You can copy and paste the code into a new text file and save as .bashrc in your home folder to restore your terminal to new.

---

### Post by Neox38 on 2007-12-08
Yay its all fixed thanks

---

### Post by Joeb454 on 2007-12-08
Lol, just coming to see if I could help but you've sorted it :P Please mark thread's as solved if they are :)

---

### Post by High Camp on 2007-12-08
Agreed on marking threads as solved. I came to see if I could help (probably not because I know nothing about the terminal).

---

