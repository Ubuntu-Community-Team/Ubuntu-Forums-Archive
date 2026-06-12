---
title: "Java mayhem"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Akis on 2007-10-24
At first I installed sun's java, but unfortunately i coudnt get the mozila plug-in working.
So I installed the icedtea jre....

currently the iced tea is causing a SIGSEGV error to azureus.:confused:
```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002aaae2a27b4a, pid=9649, tid=1074792784
#
#** Java VM: IcedTea 64-Bit Server VM** (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# C  [libglibjni-0.4.so+0xcb4a]
#
# An error report file with more information is saved as:
# /home/stelios/.azureus/hs_err_pid9649.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted (core dumped)

```

so I reinstalled sun's java, but this didn't change a thing

```
 sudo apt-get install sun-java6-jre
```
Currently neither azureus works nor many web java applets :lolflag: 
so how do i remove  icedtea or how do i use the sun's java to run azureus???
thanks in advance!

---

### Post by Sef on 2007-10-24
Simpliest way to install Java is through Add/Remove:  Applications > Add/Remove > Search > type in Sun Java 6 > Click on the top one > apply

Remove any java that you installed before would be best.

---

### Post by ItsMitsHere on 2007-10-24
before installing anything you should clean the system by **sudo apt-get clean** then update and upgrade to make your system up-to date. if you want to remove something you should type **sudo apt-get remove NameOfTheProgram** and to make sure all redundant files are removed type**sudo apt-get autoremove**... i think thats it. then you can install whatever you wish!

---

### Post by Akis on 2007-10-24
Thanks for the replies
> **Sef said:**
> Simpliest way to install Java is through Add/Remove:  Applications > Add/Remove > Search > type in Sun Java 6 > Click on the top one > apply

Remove any java that you installed before would be best.

Looks like apps installed via apt-get install aren't there :P

> **ItsMitsHere said:**
> Before installing anything you should clean the system by sudo apt-get clean then update and upgrade to make your system up-to date. if you want to remove something you should type sudo apt-get remove NameOfTheProgram and to make sure all redundant files are removed typesudo apt-get autoremove... i think thats it. then you can install whatever you wish!

Thanks a alot I finally found iced tea's "shell name" and removed it.:guitar::guitar:
```
 sudo apt-get autoremove icedtea-java7-jre
```

---

