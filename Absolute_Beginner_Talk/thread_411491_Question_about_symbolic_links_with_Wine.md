---
title: "Question about symbolic links with Wine"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by eagle101 on 2007-04-16
Hi,  I am running Feisty with the latest version of wine from Synaptic.

I'm trying to run xnews from a symbolic link from ~/.wine/drive_c/Program Files/xnews
on the desktop.  When I run it, it recreates all the folders and .ini files on my desktop, and asks for passwords, etc. again.

With windows shortcuts, you could specify a "start in" directory, I guess the windows shell would cd to the app directory before running the .exe.  Can I also do something like that with Gnome/Nautilus, or do I need to setup a shell script and run that?

Thank you for any help.

---

### Post by zvacet on 2007-04-17
in programs>accessories you have **winefile**.Click on it and you will easy find what are you looking for.I don´ know how do you install it but this way you will probably get shortcut on your Desktop.Put exe in home directory in folder named(for example) programs.

```
wine /home/programs/your_exe
```

This should give you shortcut in desktop.

---

### Post by eagle101 on 2007-04-17
> **zvacet said:**
> in programs>accessories you have **winefile**.Click on it and you will easy find what are you looking for.I don´ know how do you install it but this way you will probably get shortcut on your Desktop.Put exe in home directory in folder named(for example) programs.

```
wine /home/programs/your_exe
```

This should give you shortcut in desktop.

Hi zvacet,

The XNews distribution is just a single win32 executable file that creates directories and .ini files from wherever you happen to run it.  Kind of a nice solution for an installer-less program for windows.

I messed around with wine file (ver unknown, wine itself is 0.9.33) and found the feature Associate wasn't yet implemented.  I think that's what I wanted.   

Anyway, I'll probably just make a shell script that runs it from its' own directory.  I would like to find how to hide the terminal window when I run the script though.

Thanks for the suggestion!

Dave

---

