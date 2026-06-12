---
title: "File structure"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by a13kurt on 2007-11-13
I was wondering if anyone knew or could point me to a source to find out how the file system is setup. ex: in Windows the applications are stored in the Program Files folder. Where are the drivers stored in Linux? Installed applications? And so forth.

---

### Post by mkoehler on 2007-11-13
By searching Google for "linux file structure", I came up with this result: [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html).  It looks to be accurate, so it should answer most of your questions.  Note: The equivalent of executables on windows are bin files on linux, which are traditionally stored in the */bin directories (i.e. /bin, /usr/bin, /usr/share/bin, /sbin, etc).  Traditionally, all of the "bin" files will be placed in locations pointed to by the $PATH environment variable.  You can see all of these locations by typing ```
echo $PATH
``` in the terminal window.

Cheers!

---

### Post by erfahren on 2007-11-13
another one: [http://www.linuxcommand.org/lts0040.php](http://www.linuxcommand.org/lts0040.php)
the site itself is real informative as well.

---

### Post by a13kurt on 2007-11-17
Thank you very much. You're research is greatly appreciated.

---

