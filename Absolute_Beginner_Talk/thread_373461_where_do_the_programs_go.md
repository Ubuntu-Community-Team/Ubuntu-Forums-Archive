---
title: "where do the programs go?"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by darkchest on 2007-03-01
Sometimes, i wonder how to remove programs that i have installed from websites and are not in the synaptic manager.  I dont know if they have been added to the list or not.  I need this bcos there are some programs that dont work on my amd64 dapper.  Is there a way to keep track of what is being installed from websites?

---

### Post by Ek0nomik on 2007-03-01
Well, where do you extract the tarballs or zip files?  Personally, I created a src folder in /home/USERNAME/src.  I extract everything there, so I can keep track of what I am downloading.  Than you can run commands such as:

```
make uninstall
```...

to get rid of a specific program.  Most programs come with a README file too, telling you how to uninstall that program.  If you don't know where you put the files, try running a search for part of the name, it should find it.

Cheers!

---

### Post by darkchest on 2007-03-01
Does deleting the folder uninstall the packages?

---

### Post by actuary286 on 2007-03-01
Synaptic can only track .deb packages that you install. 

Any programs that you compile from source will not be listed. There are a few options for uninstalling programs compiled from source:

[LIST=1]
[*]Keep the original folder that you uncompressed and installed from. If you want to uninstall the program later you can go back to the same directory and run ```
sudo make uninstall
``` Unfortunately, this doesn't always work.
[*]Use the program checkinstall from the universe repository to replace the "make install" step. Checkinstall attempts to create a native .deb package for you that Synaptic can then track. Unfortunately, this also doesn't always work.
[/LIST]

If you want to install binary packages in non-deb format (i.e. .rpm or .tgz) try the program alien which is available in the main Ubuntu repositories. Alien converts non-deb packages into .deb that you can then use with Synaptic.

---

### Post by actuary286 on 2007-03-01
Which folder? If you are talking about the folder in your home directory then no, not always. Some programs will run from you home folder, but if you compile them then no. If a program does not support "make uninstall" then the other option is to find all the program files installed during "make install" and removing them manually. To find the files use:
```
whereis *program-name*
```

You will then have to delete all the files and directories that are returned.

---

### Post by Ek0nomik on 2007-03-01
What I was referring to is what **actuary286** just mentioned.  Go into the folder, and run

```
sudo make uninstall
```

Deleting the folder **will not** uninstall the program.

---

