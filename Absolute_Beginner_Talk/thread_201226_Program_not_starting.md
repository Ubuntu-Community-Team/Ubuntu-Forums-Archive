---
title: "Program not starting"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by msv240586 on 2006-06-21
Hey guys i've just installed frost wire this is how it goes:

msv240586@msv240586:~$ sudo dpkg -i FrostWire-4.10.9-2.i586.deb
(Reading database ... 62695 files and directories currently installed.)
Preparing to replace frostwire 4.9.11 (using FrostWire-4.10.9-2.i586.deb) ...
Unpacking replacement frostwire ...
Setting up frostwire (4.9.11) ...
msv240586@msv240586:~$
 But now it shows in the applications menu but when ever I click on it, it dousn't start. I've got the DEB file of it saved on my PC. What did I do wrong?

---

### Post by rowanparker on 2006-06-21
Please run *frostwire* from the terminal and show us the output,

Rowan.

---

### Post by msv240586 on 2006-06-21
what command do i use to run frostwire from the terminal?

---

### Post by rowanparker on 2006-06-21
Just put in:
```
frostwire
```
And that should work.

Rowan.

---

### Post by msv240586 on 2006-06-21
ok got it, this is what it says

msv240586@msv240586:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
msv240586@msv240586:~$

---

### Post by tronica on 2006-06-21
you need java installed, follow this guide

[http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by rowanparker on 2006-06-21
Or even easier, use Automatix.

---

### Post by msv240586 on 2006-06-21
thanks guys i'll give it a try

---

### Post by rowanparker on 2006-06-21
[QUOTE=msv240586]thanks guys i'll give it a try[/QUOTE]
No Problem :D

---

