---
title: "Where is my program?"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by arielette on 2007-07-29
[FONT="Verdana"][SIZE="2"]Hi everyone:

?  When I install a program from the synaptic package manager, I am never sure how to open it.  Sometimes it shows up in Applications but not always.  I know how to make a launcher, the problem is where is the file????  :confused:[/SIZE][/FONT]

---

### Post by atomkarinca on 2007-07-29
it's always in your home directory, like:

~./name-of-the-software

and you can type the name in a terminal window or run through alt+f2

---

### Post by Nekiruhs on 2007-07-29
> **atomkarinca said:**
> it's always in your home directory, like:

~./name-of-the-software

and you can type the name in a terminal window or run through alt+f2
... No. That is the config file directory for that program. Programs install tousr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by Daveth on 2007-07-29
the key point there is that it is a "." file. ie. hidden until you do ctrl+h, which then unhides it.
Some progs are put in /usr, of course

---

### Post by Nekiruhs on 2007-07-29
> **Daveth said:**
> the key point there is that it is a "." file. ie. hidden until you do ctrl+h, which then unhides it.
Some progs are put in /usr, of courseAgain. No. Config files are hidden. Not the program it self. If the program was hidden, you'd have to type .programname to launch it, instead of programname. Only config files and your data are stored in /home/$USER

---

### Post by Daveth on 2007-07-29
thanks- you learn something eveyday!

---

### Post by crimesaucer on 2007-09-29
Some programs install into the /opt file... like Swiftfox, or wicd, and even my Thunderbird 2.

---

### Post by southernman on 2007-09-29
The funny thing here is, the answer is ultimately in your own thread title! XD

For instance, in a terminal you type:

> whereis applicationname

If it's in fact installed, it will tell you all instances of where it is.

Other locating tools are: locate, slocate, and find... just to name a few more. Surely there are others I am not aware of yet.

---

### Post by por100pre1 on 2007-09-29
If you type in terminal:

```
which *program-name*
```

and the terminal answer something like "/usr/bin/program-name"; not only you will know where the program is located, you will ensure that you can run the program just by typing its name.

---

