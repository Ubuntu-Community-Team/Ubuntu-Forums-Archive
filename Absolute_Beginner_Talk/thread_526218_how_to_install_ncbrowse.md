---
title: "how to install ncbrowse"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by JayanthiKishore on 2007-08-15
hello

I downloaded the software "ncbrowse" software.
The software is bin file. How to install in my Ubuntu linux computer

manually I did like this
sh ./install_rel1_6_3.bin, then installed perfectly in my home directory.
after that I typed 'ncBrowse" , the command not found.

How to install this software.

---

### Post by RomeReactor on 2007-08-15
Hi. If it installed in your home folder, then it's not in your path, meaning that it's not where Ubuntu looks for executable files (like **/bin** or **/usr/bin**), so you have to specify the complete path. Look in your home directory for its folder, which is probably hidden (press CTRL+H in Nautilus to show the hidden files and folders). Once you find it, go inside that directory and look for the executable file.

The command could probably be:
```
~/.ncbrowse/ncbrowse
```

---

### Post by Hospadar on 2007-08-15
did you try "ncbrowse" often commands are all lower case.

---

