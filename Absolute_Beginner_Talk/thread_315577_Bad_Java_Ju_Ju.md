---
title: "Bad Java Ju Ju"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2006-12-09
I recently re-installed Ubuntu 6.06 and in setting it up used Automatix2 to download and install Java-1.5.
 Now every time I add or remove anything with the terminal I get the message below. In this example I was installing deborphan using 'aptitude'
```
Fetched 289kB in 4s (59.7kB/s)
 Selecting previously deselected package dialog.
 (Reading database ... 118027 files and directories currently installed.)
 Unpacking dialog (from .../dialog_1.0-20060101-1_i386.deb) ...
 Selecting previously deselected package deborphan.
 Unpacking deborphan (from .../deborphan_1.7.18_i386.deb) ...
 Selecting previously deselected package gtkorphan.
 Unpacking gtkorphan (from .../gtkorphan_0.4.1-1_all.deb) ...
 Setting up sun-java5-doc (1.5.0-06-1) ...
 This package is an installer package, it does not actually contain the
 J2SDK documentation.  You will need to go download one of the
 archives:
 

     jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip
 

 (choose the non-update version if this is the first installation).
 Please visit
 

     http://java.sun.com/j2se/1.5.0/download.html
 

 now and download.  The file should be owned by root.root and be copied
 to /tmp.
 

 [Press RETURN to try again, 'no' + RETURN to abort]

``` I need help with this-- I want to undo the Automatix2 installation that started all this.

---

### Post by lonce on 2006-12-09
start automatix and use the uninstall function on the java with automatix.  Then see if the error continues.

---

### Post by kindafunnylookin on 2006-12-09
Good idea, but I have tried that. The message that I get is
> Automatix2: Error and Information Report
Information: SUN JAVA 1,5jre
An apt based error occured and unstallation was unsuccessful.

---

### Post by kindafunnylookin on 2006-12-09
Thread closed. I re-installed.

---

