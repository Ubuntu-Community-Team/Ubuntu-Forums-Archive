---
title: "How can I make an alias in KDE or in the terminal?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-05-04
I'm using KDE and an alias of my home folder on the desktop. How can I do this?
Thanks!

---

### Post by igknighted on 2007-05-04
Do you want an alias or a shortcut?  To make a shortcut, simply right click the desktop and add a shortcut to a folder, then specify it to point to the home folder.  If you want an alias you will need to explain further, as an alias typically refers to a command on the command line being "forwarded" if you will to another command.

---

### Post by Xarok on 2007-05-04
> **igknighted said:**
> Do you want an alias or a shortcut?  To make a shortcut, simply right click the desktop and add a shortcut to a folder, then specify it to point to the home folder.  If you want an alias you will need to explain further, as an alias typically refers to a command on the command line being "forwarded" if you will to another command.

It seems like KDE can only make a link to a file or app, but not a directory.

Yes I've heard of alias in reference to the terminal.
Under OSX (which I also use a lot) links are called aliases. Sorry for using the wrong terminology.

---

### Post by Austin_KW on 2007-05-04
A directory is a file, so you can create a link to it. Easiest way is using a terminal

Open a terminal (under utilities menu)
change to the desktop directory with the command "cd Desktop"
then create a softlink to your home directory " ln -s /home/*myUserNameHere* ./myHomeDir"

myHomeDir (or whatever you called the link) should pop up on your desktop

---

