---
title: "Help with Symbols  / _ . ect"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by jazzman84116 on 2007-05-29
Is there a web site or that explains what the Symbols  mean

---

### Post by Brunellus on 2007-05-29
[www.linuxcommand.org](www.linuxcommand.org)

In general:

~/ is your home directory.  Mine would be /home/brunellus for example.

/ is the separator that shows directories.  / all by itself is the ROOT filesystem.  everything else branches off from that.

\ (backslash) is an escape character.  we use the backslash to "escape" certain characters so that the shell will interpret what we mean correctly.  You'll usually see this in directories with long names that also contain spaces.

Say you have a directory named "My Really Really Really Cool Stuff" in your home directory.  if you're in the command line, and you try to change to that directory, you might try this at first:

cd ~/My Really Really Really Cool Stuff

Of course, that will fail, since the shell will only process as far as "My" and ignore everything after the space.  What to do?  we use backslashes!

cd ~/My\ Really\ Really\ Really\ Cool\ Stuff

and behold!  you're there.

---

### Post by Sparkster185 on 2007-05-29
I would suggest you read an introduction to the Bash Shell.  It should explain what all those mean.

When navigating directories, the "." means the current working directory.  So, if you are in your home and you have a folder called "music", then you could do the following

```

cd ~
cd ./music

```

This is especially useful when executing commands or scripts without having to specify an absolute pathname.  Alternatively, ".." means up one directory. So you can do things like 
```

cd ~
cd ./music
cd ..

```
and you would be back in your home directory.

---

### Post by Bosonator on 2007-05-29
You might find some infor here:

[https://help.ubuntu.com/7.04/basic-commands/C/index.html](https://help.ubuntu.com/7.04/basic-commands/C/index.html)

To answer your question in brief, though:

The symbol / designates a directory. On its own it is the "root" directory, where your Ubuntu system is stored. After a name, it designates that name as a directory (e.g. home/ Desktop/ or Music/).

The symbol . means "here", or "in the present directory". The symbol .. means "one directory up" or "the parent directory".

The symbol . can also go in front of any filename to make it a hidden file. You probably have a directory in your home directory called .mozilla/ if you use the firefox browser. It's hidden because it contains configuation options that you wouldn't normally need to access. 

The symbol _ is an "underscore" and doesn't have any special meaning to my knowledge. It's just used in place of a blank space.

Hope that helped!

---

