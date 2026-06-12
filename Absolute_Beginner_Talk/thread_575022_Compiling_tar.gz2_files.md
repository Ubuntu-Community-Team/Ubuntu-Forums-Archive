---
title: "Compiling tar.gz2 files?"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Taters on 2007-10-13
I'm trying to compile a newer version of Gimp (2.2.17 Synaptic has 2.2.13) but I have an extremely basic knowledge of Linux n' Things.


If anyone could tell me how to do this, that'd be really dandy. I have to leave very soon, so you will probably see me bumping this to answer somethings.

(I'm running 7.04)

Thanks,

-Taters

---

### Post by useResa on 2007-10-13
Basically you do not compile the tar.gz2 file. This is basically just a sort of "zip" file.
So, the first step you have to take is to "unzip" this file.
This is easiest done by double clicking the file and you will get a window in which you can indicate where the files are to be extracted.

Now you have a directory in which you can start the actual compilation. There are quite clear instructions on how to do this on the [GIMP - Install help page]("http://www.gimp.org/downloads/install_help.html").

An other option is to download a .deb file. If you have GDebi installed, this will "automatically" install the software and resolve any dependency issues. You can find a .deb file for GIMP 2.2.17 [here]("http://packages.debian.org/lenny/gimp/i386/download").

---

### Post by Taters on 2007-10-13
Wow... Thank you!


I should probably look more into this. Thanks again!

Er... It says Dependency is not satisfiable: Gimp-Data

? Please help.

---

### Post by useResa on 2007-10-14
For Gimp 2.2.17 you need the matching Gimp data file.
The deb file can be downloaded from [this location]("http://packages.debian.org/lenny/gimp-data/all/download").
I suggest you install this one first.
 
If you need other Gimp files, all Gimp related files can be found [here]("http://packages.debian.org/lenny/gimp").
 
Another option is to edit your /etc/apt/sources.list file as indicated on each of the indicated locations. This way you will have a location from which the dependencies can be resolved.

---

