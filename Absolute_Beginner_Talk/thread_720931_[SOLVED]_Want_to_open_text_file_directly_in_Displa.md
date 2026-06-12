---
title: "[SOLVED] Want to open text file directly in Display mode"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by gobuntu on 2008-03-10
Dear friends,

Since I use short text files a lot for documentation, and I don't forsee clicking on text files to execute them:

1. Can one set-up options somewhere so that when clicking on a text file, it opens immediately in the Display Mode, where I can both read it and edit it?

As it is now, when clicking on a text file I have to go to a drop down menu that asks if one wants to execute it or open it in the display mode.

I would like very much to avoid that choice and open text files directly in the display mode.

Text file scripts, for execution,  I would cut-paste into a terminal, when so needed.

Thanks!

---

### Post by scragar on 2008-03-10
you could just remove the execute permissions on them(via properties and uncheck execute, or the command line:```
chmod -x **FILE**
```replacing FILE with your files path/name

---

### Post by PurposeOfReason on 2008-03-10
The only way I would know about doing that would just to use the terminal to open up the editor so like

gedit /path/to/file
OR
sudo gedit /path/to/file

if you need to be root.

> **scragar said:**
> you could just remove the execute permissions on them(via properties and uncheck execute, or the command line:```
chmod -x **FILE**
```replacing FILE with your files path/name

Then he couldn't execute them later.

---

### Post by argraff on 2008-03-10
[Nope - here's a way!]("https://help.ubuntu.com/7.10/user-guide/C/nautilus-preferences.html")

Go into Edit > Preferences when in a Nautilus window, choose the 'Behavior' tab, and it's in there...I thought I saw that somewhere!

---

### Post by gobuntu on 2008-03-10
> **argraff said:**
> [Nope - here's a way!]("https://help.ubuntu.com/7.10/user-guide/C/nautilus-preferences.html")

Go into Edit > Preferences when in a Nautilus window, choose the 'Behavior' tab, and it's in there...I thought I saw that somewhere!

YES!

Thats exactly what was needed.

Now one click on the file's icon is all it takes.

Thanks a lot!

OK: Will add that, one reason why it's not THAT clear is that the option reads: "View EXECUTABLE text files when they are opened". That's the option to select, and that, of course applies also to NON-EXECUTABLE text files!

And, quoting now from the Documentation, which could be improved: *"View executable text files when they are clicked.  Select this option to display the contents of an executable text file when you choose the executable text file".*

---

### Post by lu6cifer on 2008-04-15
thanks for this...I had the same problem..

---

