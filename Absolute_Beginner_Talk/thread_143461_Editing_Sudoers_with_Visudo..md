---
title: "Editing Sudoers with Visudo."
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by GarethMB on 2006-03-12
I've been trying to edit the Sudoers file to add this command to the list :

```
username ALL= NOPASSWD: /usr/bin/firestarter
```

But so far i've had absolutely no luck infact, afaik i've just created a load of 'backup sudoers files' -Wack.

[[IMG]http://img440.imageshack.us/img440/1452/screenshot2dp.png[/IMG]](http://imageshack.us)

On top of that i've even managed to create some pseudo sudoers files in my home directory.

I want to know 3 things
[LIST]
[*]How do I actually edit the sudoers file (step by step instructions please) to add firestarter to the group that doesn't need root permissions?
[*]Can I delete all the annoying backup sudoers files?
[*]If i can delete these files how do I do it?
[/LIST]

---

### Post by mlind on 2006-03-12
use this command from terminal
```

sudo visudo

```

to enter edit mode on vi-editor, press 'i'
then use cursor keys to move at then end of the file,
enter the command you already posted as last line on that file.
note that NOPASSWD entries must be the last on this file.
then press ESC  (to exit edit mode)
then enter command :wq  (to save and exit the editor)

you can delete backup entries doing *sudo rm (filename)*,
but those are there for a reason.. you should at least
keep backup of the original sudoers file

---

### Post by GarethMB on 2006-03-12
i've just noticed that sudo visudo opens nano 1.3.8 i think, im guessing that means i don't have visudo installed. How do i install visudo?

---

### Post by mlind on 2006-03-12
it should be installed. does following command give you its location?
```

whereis visudo

```

you have probably EDITOR environment variable set? 
```

set | grep -i editor

```

try to unset it, or define this to visudo
```

unset EDITOR

```

---

### Post by taurus on 2006-03-12
[QUOTE=GarethMB]i've just noticed that sudo visudo opens nano 1.3.8 i think, im guessing that means i don't have visudo installed. How do i install visudo?[/QUOTE]
Maybe you set "nano" as your default text editor!!!

---

### Post by mlind on 2006-03-12
I guess you can edit sudoers file with any editor, just as long you are doing
it using *visudo* command. Is this correct?

Visudo is only wrapper for providing locking and validation for sudoers file.

if you prefer nano editor, then set EDITOR variable as 
```

export EDITOR=nano

```

---

### Post by GarethMB on 2006-03-12
I'm still having no luck. Here is the response to whereis:

gareth@ubuntu:~$ whereis visudo
visudo: /usr/sbin/visudo /usr/share/man/man8/visudo.8.gz

and here is the response to sudo visudo

> 
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
                               [ Read 22 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell


When i press 'i' I just add the letter 'i' at the begging of the document.

I can insert the text at the bottom:

gareth ALL= NOPASSWD: /usr/sbin/firestarter

After that if i press Esc. Nothing obvious seems to happen.

The typing either :wq or command :wq has no effect.

What is wrong ; ;

---

### Post by taurus on 2006-03-12
You are using nano as your text editor so don't have to worry about i or esc key.  Just use the down arrow key to move down to where you want to insert and type it in.  Then, hold down <Ctrl>x to save and exit it.  Press Y when it asks if you want to save it...

---

### Post by GarethMB on 2006-03-12
Thanks! Problem solved.

---

