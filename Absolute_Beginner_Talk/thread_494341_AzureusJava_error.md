---
title: "Azureus/Java error"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by muggins on 2007-07-06
When I try to start azureus it starts to open and then closes in about 10 seconds if that. I get the following error in terminal.

         # An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb4899172, pid=7578, tid=3085069200
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9172]
#
# An error report file with more information is saved as hs_err_pid7578.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)

I don't know what I should try to do at this point, any suggestions?

---

### Post by Rocket2DMn on 2007-07-06
Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=481318](http://ubuntuforums.org/showthread.php?t=481318)
NeoLithium suggests:
1) Go into your /home/USERNAME/.azureus folder and delete all the logs
2) Double check that your computer is still using sun java as an option with this command in terminal: sudo update-alternatives --config java

I have seen both these solutions work, I suggest starting with deleting the logs.

---

### Post by toasterofirony on 2007-07-06
Or install Ktorrent. That works pretty well too.

---

### Post by muggins on 2007-07-07
Found a solution at the launchpad bug entry: [https://bugs.launchpad.net/ubuntu/fe...eus/+bug/68020](https://bugs.launchpad.net/ubuntu/fe...eus/+bug/68020).

 Mike Fedyk said on 2007-06-20: (permalink)

After reading this ([https://wiki.ubuntu.com/Bugs/HowToTriage](https://wiki.ubuntu.com/Bugs/HowToTriage)), bugs should be marked duplicate if they have the same root cause, even if they have different symptoms.

If azureus doesn't crash after the fix for bug 57875 is committed on a feisty system with the azureus in feisty-proposed and xorg+sun-java5 or xorg+sun-java6, then this bug is a duplicate. Even if they crash at different times (splash screen or sliding alert message).

What I need is for everyone with a feisty system to install the azureus package in the feisty-proposed repository or from this link:
[http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb)

What I did was uninstall azureus and download this one from the above link.

---

