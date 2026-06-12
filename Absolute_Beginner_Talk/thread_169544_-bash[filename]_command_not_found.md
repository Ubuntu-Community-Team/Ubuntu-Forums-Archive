---
title: "-bash:[filename]: command not found"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by zappadragon on 2006-05-02
-bash: [filename]: command not found

this is the error i get when I try to run a script or any file in my home directory. When I first ssh into my Ubuntu box. If i do a . .profile then I can run the script or file.

---

### Post by Foxmike on 2006-05-02
Does the user with wich you ssh on your Ubuntu box have permissions to execute the files you want to?

> foxmike@ubuntu:~$ ls -l
total 71
drwxrwxrwx  3 foxmike foxmike ... "filename"

If you don't have permissions, you cannot execute it.

Regards,

-FM

---

### Post by BoneKracker on 2006-05-02
Check your path.  It's probably not what you assume it to be at the time you are issuing the command.

For example, that is the same error often generated when a regular user forgets to prefix a command with sudo.  The first error often encountered seems is that the file isn't even accessible via their path, so instead of getting a "you don't have privileges" type error, they get a "file not found" type error.

---

### Post by zappadragon on 2006-05-02
no I do hav rwx permissions on that file and it does not work when I first login but if I do a . .profile my command line changes and then I can run the file. If I do a PWD it is the same before and after I do the . .profile. Can someone please post a sample of there .profile to make sure I have my .profile setup right

thanks

---

### Post by zappadragon on 2006-05-02
OK so it seems to be my path maybe? here is my path:

PATH=$HOME:$HOME/bin:/usr/bin:/bin:/usr/local/bin:/usr/gnu/bin:/usr/bin/perl.
export PATH

my files are in my home dir 

what am I doing wrong?????

---

### Post by zappadragon on 2006-05-03
what am I doing wrong? here is a copy of my .profile

stty erase ^H

# Set keyboard to simulate vi functions.
set -o vi

# Set default editor to vi
EDITOR=/usr/bin/vi
export EDITOR

PS1='imac@ubuntu:[$PWD~$]'
export PS1

PATH=$HOME:$HOME/bin:/usr/bin:/bin:/usr/local/bin:/usr/gnu/bin:/usr/bin/perl.
export PATH


set -o vi # enable the ability to recall previous commands with <Esc><k>


when I log in this is my prompt:
imac@ubuntu:~$

when i do a . .profile it changes to this:
imac@ubuntu:[/home/imac~$]

then I can run my files

please help

thanks

---

### Post by nanotube on 2006-05-03
try the following command:
```
cp .profile .bashrc
```
see if that makes your settings take effect properly.

---

### Post by zappadragon on 2006-05-03
**YES that worked. thanks so much!**

now can you tell me what that did. I am new to unix/linux and this box is my study guide.

thanks again

---

### Post by zappadragon on 2006-05-03
OK so what happened to the colors? not that its that big of a deal but it was a nice feature. All my files now are just white when before I ran that command I had some blue green red and white

thanks

---

### Post by zappadragon on 2006-05-03
I added this alias and that seemed to fix it

alias ls='ls --color=auto'

---

### Post by nanotube on 2006-05-03
[QUOTE=zappadragon]**YES that worked. thanks so much!**

now can you tell me what that did. I am new to unix/linux and this box is my study guide.

thanks again[/QUOTE]
well, .profile is triggered "on login", and .bashrc is triggered every time you start a bash shell. so i figured, if .profile is not being triggered for some reason, stuff it in the bashrc, and its bound to be used, cuz a bash shell is gonna be started. :)

---

