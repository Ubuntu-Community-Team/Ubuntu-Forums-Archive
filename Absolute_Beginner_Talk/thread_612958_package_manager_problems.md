---
title: "package manager problems"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by falconsdive on 2007-11-14
when i try to update my computer i get this error in the manager:
     E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
     E: _cache->open() failed, please report.
so, i type "sudo dpkg --configure -a" and it tells me that i need to download java.  but when i download the file i can't open it.

help please!!!

---

### Post by DutyDuty on 2007-11-14
How are you trying to update? Is Synaptic, Add/Remove and/or Automatix open?

---

### Post by falconsdive on 2007-11-14
i'm using the synaptic package manager.

---

### Post by Inxsible on 2007-11-14
Open a terminal and then type in ```
sudo dpkg --configure -a
``` Make sure you close synaptic before you do this.

---

### Post by falconsdive on 2007-11-16
i typed "dpkg --configure -a" and this came up:

Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

but that file is just documentation not the actual java file.  so, with the instruction of my profesor, i downloaded this file:  jdk-6u3-linux-i586.bin

but when i try to open this file, i get this error in Envice Document Viewer:

Unhandled MIME type: “application/x-shellscript”

I have a complicated problem, don't I (lol!)

---

### Post by por100pre1 on 2007-11-16
Unless intentionally using Java Development Kit you don't need that package. If you just use Java Runtime Environment you can just remove it like this:

```
sudo apt-get remove sun-java6-doc
```

EDIT: You don't need sun-java6-doc at all, just have JDK installed like this:

```
sudo aptitude install sun-java6-jdk
```

---

