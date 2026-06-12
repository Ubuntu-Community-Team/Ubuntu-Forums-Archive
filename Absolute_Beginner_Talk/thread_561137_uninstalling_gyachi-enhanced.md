---
title: "uninstalling gyachi-enhanced"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Roque2 on 2007-09-27
hello  I have a small favor to ask someone, Would someone please show me the command to remove this gyachi-enhanced and gyache-webcam off my computer please. These are the file names  gyach-enhanced_pyvoice-binary-1.0.7-i586.tar.bz2 and gyachE-Webcam-Utilities-0.4-i586.tar.bz2

---

### Post by Hospadar on 2007-09-27
Did you build the software from source (with a series of commands like "./configure make&&make install")?  If that's the way you did it, you will probably want to get to a command line, cd to where you extracted the code (if you deleted that folder, re-extract the code from each *.tar.bz2 file into seperate folders) and then do a ```
sudo make uninstall
```  If whoever wrote your software put in an uninstaller script, this is probably how you would use it.

If you installed the software some other way, please let me know exactly what commands you used.  It may be that you need to reinstall the software and watch carefully the output of the "make install" command so you know exactly what files it created, and then hunt down and individually delete all the files. but that should be a last resort.  almost all software has a "make uninstall" option.

---

### Post by Roque2 on 2007-09-27
I got it from the phrozensmoke.com site and I installed it doing the tar -xjf gyach-enhanced_pyvoice-binary-*-i586.tar.bz2

---

### Post by Roque2 on 2007-09-27
sorry for being a noob

---

