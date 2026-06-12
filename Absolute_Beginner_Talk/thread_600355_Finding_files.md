---
title: "Finding files  ??"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by thelugnut on 2007-11-02
I don't seem to be getting much smarter here.

The situation now is,I can't find stuff.

Example: I have the Python 2.5 on my computer. I run it, with no problems.

But I have not a clue where it is, nor how to find it.

I have searched as well as I know how with no luck at all.

So, how do you find stuff with Ubuntu?

:confused::confused::confused:

---

### Post by mikewhatever on 2007-11-02
Try the terminal
> sudo updatedb
locate file_name

---

### Post by thelugnut on 2007-11-02
Thank you very much

---

### Post by erginemr on 2007-11-02
In addition to 
"locate python"
above, you may also use the following commands to find files from the console:

To find the location of a binary (program): which python

To find all files containing a keyword in their name: whereis python

To get more information about what a command or program does: whatis python
(which shows actually the desctiption part of the man page for python, which you can also view with: man python)

To get a list of all the installed programs related to a topic: apropos python

Finally, the default Gnome file finder is also good at locating files in your computer.
"Main Menu -> Places -> Search for Files..."
(But you need to specify the search path as your file system first.)

---

### Post by thelugnut on 2007-11-02
Thank you , I really appreciate all the help I have been receiving.

---

### Post by philinux on 2007-11-02
Also in synaptic if you click on an installed package you will see a tab for installed files - here you can see what went where.

---

### Post by mali2297 on 2007-11-02
If you want to find the location of the executable, try **which** or **whereis**. For example:
```

which python

```

If you don't know the exact command that starts the program, try **apropos**:
```

apropos python

```
This will show every command that contains "python" in its description.

---

