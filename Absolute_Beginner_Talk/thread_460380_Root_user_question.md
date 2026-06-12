---
title: "Root user question"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by FourZeroFour on 2007-05-31
I installed apache2 and php5 on ubuntu 7.04 and I am trying to put some files on to the server. When I try to save files to the directory it tells me I do not have premission. There is only one user set up on this machine and no root. I am new to this so maybe I am over looking something..

---

### Post by Ek0nomik on 2007-05-31
You are trying to use a command to do it I take it?

Put "sudo" in front of your command.

---

### Post by FourZeroFour on 2007-05-31
actually I was just trying to save the file from text editor, thanks for the quick reply

---

### Post by Cypher on 2007-05-31
You probably started the text editor as a regular user, so that won't work..open up a terminal and type "gksudo gedit" and then you can create/safe files in the /var/www directory without any problems..

---

### Post by irish_flu on 2007-05-31
You can "sudo" the copy command to copy the files.

For instance,
```

sudo cp /home/irish_flu/thefile.txt /etc/thefile.txt

```
will copy the file from my home directory to the /etc directory.  the "sudo" gives me super-user rights.



Alternatively, if you want to do this with the GUI file browser you can do that too.
in the command line, type
```

gksu nautilus

```
This will open up a file browser window with root rights.

I used "gksu" here instead of "sudo" because I'm told that "sudo" is for doing command-line stuff as root, and "gksu" is for doing GUI (gnome) stuff as root.

hope this helps!

EDIT: LOL, sorry for the redundant reply; I answered a telephone call while in the middle of typing, and these other folks beat me to the punch....

---

