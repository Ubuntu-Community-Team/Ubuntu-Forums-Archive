---
title: "Frostwire won't run anymore"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2008-01-11
I have Frostwire installed and when I try to click on it it won't run. If I run Frostwire in the terminal I get
```
~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com

```
but I do have Java installed because Limewire will run (But Limewires much more slow so I don't like to use it.)
I've already tried reinstalling Java and Frostwire but It didn't work.
Does anyone know whats going on?

---

### Post by taurus on 2008-01-11
What's the output of this command from a terminal?

```
java -version
```

---

### Post by microsoft92sucks on 2008-01-11
[CODE[:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
[/CODE]

---

### Post by taurus on 2008-01-11
You need Sun java, not the gij version.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin 
java -version
```

---

### Post by microsoft92sucks on 2008-01-11
I'm still getting the same output for
```
java -version

```
Should I remove the gij java... Because I have and had sun java installed. But it seems that my computer is using gij instead. So would removing gij fix this?

---

### Post by microsoft92sucks on 2008-01-11
okay I removed gij and frostwire works now.
Thanks for the help.

---

### Post by taurus on 2008-01-11
Run

```
sudo update-alternatives --configure java
```
and pick the latest version, 1.6 from the list, as your default.

---

