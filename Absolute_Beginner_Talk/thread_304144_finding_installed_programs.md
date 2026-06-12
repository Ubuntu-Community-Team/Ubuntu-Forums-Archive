---
title: "finding installed programs"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Carolyn62 on 2006-11-21
Hi,

 I installed 2 programs through synaptic. Gparted and beagle search. Problem is that beagle search is supposed to be accessible through applications> accessories> beagle search, according to "The official Ubuntu book" page 202. Well its not there and I do not know how to find it.

As for gparted I can't find it either, so how do I access it?. I know that I am new at this and am trying to learn. I have gotten this far with Ubuntu with a little help from you folks and I hope my questions do not sound dumb.

If I may there is one more small problem I am having in the terminal:

In following the official "book" on page 142 it is showing me how to use the terminal. In the getting started section it tells me to type in:

foo@bar~$ 1s and what I get is:

blank@tux:~$ foo@bar~$ 1s
bash: foo@bar~$: command not found
blank@tux:~$

so then I tried:

blank@tux:~$ foo@bar~$ ls
bash: foo@bar~$: command not found
blank@tux:~$

I tried foo@bar~$ cd desktop and got:

blank@tux:~$ foo@bar~$ cd desktop
bash: foo@bar~$: command not found
blank@tux:~$

So I believe that I am following directions, just no reward. Can anyone help?

Carolyn

---

### Post by Amit Yaron on 2006-11-21
1. Seems to me that you should drop the "foo@bar~$" from the commands you type.
2. I have GParted installed in my System, and I find it in:
application->system tools->GParted.

---

### Post by Carolyn62 on 2006-11-21
> application->system tools->GParted

I do not have a systen tool in applications.

Also:

> Seems to me that you should drop the "foo@bar~$" from the commands you type.

Thank You, This seems to work. I forgot to mention that I am using dapper.

Now if I can find Beagle and gparted I would be most happy (gee, it does not take much)

Carolyn

---

### Post by yanqui on 2006-11-21
I'm experiencing a similar problem with a dial-up program; I've installed it, and I would think that it would be under Applicaitons>Internet.  I've been EVERYWHERE.  It is an installed program, when I go to the add/remove list, it's there.  I just can't find it to use it.

---

### Post by smoker on 2006-11-21
try right clicking on applications, and select edit menus, and check the options available there

---

### Post by Amit Yaron on 2006-11-21
I think dial-up should be under "system tools", under "Internet" you can find web applications such as Fiefox, Evolution, Gaim (Instant Messaging), etc.

---

### Post by yanqui on 2006-11-21
> **Amit Yaron said:**
> I think dial-up should be under "system tools", under "Internet" you can find web applications such as Fiefox, Evolution, Gaim (Instant Messaging), etc.


That was the first place I looked.  I promise you it's not there.

Nor did it show up in the alacarte menu editor options.

---

### Post by yanqui on 2006-11-21
> **yanqui said:**
> That was the first place I looked.  I promise you it's not there.

Nor did it show up in the alacarte menu editor options.

Okay, I found the "add" thingie.  Now--and please remember that I AM a new user--what is the command extension for a program to launch?  Like in Windows it would be .exe; what is it for Linux?

---

### Post by Carolyn62 on 2006-11-21
> try right clicking on applications, and select edit menus, and check the options available there

OK smoker, I found gparted (Thank You), But beagle is no where to be found. Should I reinstall it again (thru synaptic again)?

Carolyn

---

### Post by Amit Yaron on 2006-11-21
> **yanqui said:**
> Okay, I found the "add" thingie.  Now--and please remember that I AM a new user--what is the command extension for a program to launch?  Like in Windows it would be .exe; what is it for Linux?

No extensions. It should have execute permissions, and the correct magic number (e.g. a bash script should begin with the line '
#!/bin/bash'.
In additon, the file should be located in one of the directories in $PATH (separated by colons).

To determin whether the file is executable run the command
ls -l foo

and you will see a line such as:
-rwxr--r--  1 owner group 104 2006-11-14 20:42 foo

Look at the rightmost field of the output line
----------------------------------------------
The first character determines if the file is a directory, symbolic link, flat file, etc.
Flat files have '-'.

The following 3 characters are the owner's permission (Read, Write, eXecute).
4th to 7th characters: group's permissions.
8th to 10th charaters: other users' permissions.

---

