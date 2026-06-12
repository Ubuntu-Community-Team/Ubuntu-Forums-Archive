---
title: "Command Line"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2007-10-20
I am trying to learn the Command Line. I have made a new directory but haven't a clue how to move files from my desktop into the new directory. Hope someone will help. Thanks

---

### Post by Qwerty_ on 2007-10-20
Perhaps this will help you.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by davidjxyz on 2007-10-20
Note that the desktop is just a directory in your home directory called "Desktop". Try this from your home directory

$ ls Desktop

or:

$ cd Desktop
$ ls

To move files from the Desktop to your new directory try this:

$ mv Desktop/[myfile] [mydirectory]

replacing [myfile] and [mydirectory] with the appropriate names for your system.

Note that tab-completion makes life a lot easier in the command-line. Type the start of a name then hit tab, if it's unambiguous what the remainder is then it will be filled in. If it's ambiguous then the options will be shown. Type a few more characters to make it unambiguous then hit tab again. Try this a few times and you'll see what I mean.

e.g.

$ cd Desk[tab]    -    will be completed to read "Desktop"

Also, the command-line uses spaces to separate commands and file names. If you have spaces in file names it gets confused and these have to be escaped (made non-special). You do this by putting a backslash before them. So you'll have:

$ ls My\ Special\ Folder

Tab-completion does this automatically.

Hope this helps a bit.

---

### Post by oscarthefish on 2007-10-20
Alright thanks guys

---

