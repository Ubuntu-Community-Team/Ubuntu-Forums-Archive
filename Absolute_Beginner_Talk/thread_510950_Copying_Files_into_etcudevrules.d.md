---
title: "Copying Files into /etc/udev/rules.d"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by colinpat on 2007-07-27
I am trying to copy a file (10-local.rules) into the folder /etc/udev/rules.d b ut system says I do not have permission.  How do I give myseld permission to do this?

Thanks

---

### Post by Foxmike on 2007-07-27
```
sudo cp <name-of-the-file-to-be-copied> /etc/udev/rules.d
```
See the "sudo" at the begenning.   This is what will give you the super-user permissions.  When asked for a password, it is your login password.
 
Note that when doing tasks with sudo, you better make sure this is really what you want to do and you know whay you are doing.

---

### Post by colinpat on 2007-07-27
Thanks Foxmike.

File is currently in /home/colin/Data Files would I be correct with
sudo cp /home/colin/Data Files/10-local.rules /etc/udev/rules.d

---

### Post by Foxmike on 2007-07-27
> **colinpat said:**
> Thanks Foxmike.
 
File is currently in /home/colin/Data Files would I be correct with
sudo cp /home/colin/Data Files/10-local.rules /etc/udev/rules.d
Almost and close!:)  here is the proper command line:
```
sudo cp ~/Data\ Files/10-local.rules /etc/udev/rules.d/
```
The "~" is a shortcut to "/home/<name-of-the-current-user>" and refers to your "home" directory.  Typing it long would have done the same thing, but I always like to add a little +!;)
 
Note the "\" before the space.  This is very important as the space (and some other characters) has special meaning in the shell.  the "\" stantds to "escape-next-character-please-and-read-it-textually" for the shell.
 
A last detail, beware that the shell is case-sensitive.
 
Hope it helps!:)

---

### Post by colinpat on 2007-07-27
Many thanks Foxmike - worked ok.  I actually changed the directory from data files to data_files and got it to work that way.
Again many thanks
cp

---

### Post by Foxmike on 2007-07-27
Very welcome and welcome onboard!:)

---

### Post by Mornedhel on 2007-07-27
Quick note for colinpat :

An extremely handy feature of bash and many other shells is the autocompletion of (among other things) filenames.

You can use it by pressing the tab key in the middle of a filename, at which point it will attempt to complete it as far as possible. Works with some other things :

- usernames
- commands
- even some command arguments

Pressing tab twice will display a list of possibilities. Autocompletion is really useful when dealing with weird characters.

---

### Post by Foxmike on 2007-07-27
> **Mornedhel said:**
> Quick note for colinpat :
 
An extremely handy feature of bash and many other shells is the autocompletion of (among other things) filenames.
 
You can use it by pressing the tab key in the middle of a filename, at which point it will attempt to complete it as far as possible. Works with some other things :
 
- usernames
- commands
- even some command arguments
 
Pressing tab twice will display a list of possibilities. Autocompletion is really useful when dealing with weird characters.
And to add on that, if there is several choices, taping tab twice list you those choices.  Beauty of command line!:guitar:

---

