---
title: "problem trying to run limewire and frostwire"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by fonzcorp on 2007-06-12
just switched to ubuntu this week. been loving it.

heres my problem when trying to run limewire and frostwire
```

fonz@Linux-Fonz:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
fonz@Linux-Fonz:~$ frostwire
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
fonz@Linux-Fonz:~$ 
```

from what it looks like. the software is having an issue trying to find java. i think i already have the latest java but not completely sure. so i tried installing the RPM self exctractor from java.com last night. i spent all night...didnt work out for me. anyone can help me out? searched the Feisty guide, and the forums.

---

### Post by Hobo Joe on 2007-06-12
First, I'd recommend a clean install of Frostwire:
```

sudo aptitude purge frostwire

sudo aptitude install frostwire

```

If that doesn't work, you should probably re-install java. But sadly, I can't help you there, java comes in like.... a hundred different packages....

---

### Post by Fidelio on 2007-06-12
I had this problem and I took the cheat's way out and installed Frostwire through automatix. Some decry automatix, but it worked a treat for me.

---

### Post by gigaferz on 2007-06-12
im not a linux pro but, i dont think you should be doing it with a RPM package.....

try the other option
[http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)

I dont remember how i did it, but if that is too complicated, just get automatix, is as esay as clicking, 

and yes, right now just unistal frostwire, once youre ok  to go, install it,,

If you have frostwire you (i think) do not need limewire.

---

### Post by gigaferz on 2007-06-12
hey, try this

sudo apt-get install sun-java6-jre

enabling multiverse repositories

---

### Post by fonzcorp on 2007-06-13
i resulted in using automatix. is worked. installed java. then did a clean install of frostwire. its runs fine. but now my azureus is giving me problems:
```

fonz@Linux-Fonz:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=3420, tid=3084241808
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid3420.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
fonz@Linux-Fonz:~$ 

```

something now seems to be conflicting with azureus.

---

### Post by zvacet on 2007-06-13
synaptic>search box <type** sun** and you will find every available Java version there.Pick one you want and install it.

---

### Post by fonzcorp on 2007-06-13
no fixes for my azureus problem>?

---

### Post by gigaferz on 2007-06-13
[http://ubuntuforums.org/showthread.php?t=435935&highlight=azureus+crashes](http://ubuntuforums.org/showthread.php?t=435935&highlight=azureus+crashes)

i remember unistalling everything and then doing everything agin,,,so give it a try 
go to synaptic package manager and uninstall azureus with all the dependencies..
then reinstall,,,,

---

