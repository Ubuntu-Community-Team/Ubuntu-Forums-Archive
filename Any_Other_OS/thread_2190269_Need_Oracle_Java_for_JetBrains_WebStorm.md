---
title: "Need Oracle Java for JetBrains WebStorm"
date: 2013-11-25
forum: Any Other OS
---

### Post by randumfaktor on 2013-11-25
I need JetBrains WebStorm which requires Sun Java.  I just ran the instructions at [ http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html") without any errors or difficulty. I'm running Linux Mint Petra RC1 64-bit on a Dell Inspiron 17-3721GQPI3.

Commands run:

```
[INDENT]sudo add-apt-repository ppa:webupd8team/java[/INDENT]
[INDENT]sudo apt-get update[/INDENT]
[INDENT]sudo apt-get install oracle-java7-installer[/INDENT]

```
Result from "update-alternatives --query java"[INDENT]Name: java
Link: /usr/bin/java
Slaves:
 java.1.gz /usr/share/man/man1/java.1.gz
Status: auto
Best: /usr/lib/jvm/java-7-oracle/jre/bin/java
Value: /usr/lib/jvm/java-7-oracle/jre/bin/java


Alternative: /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java
Priority: 1071
Slaves:
 java.1.gz /usr/lib/jvm/java-7-openjdk-amd64/jre/man/man1/java.1.gz


Alternative: /usr/lib/jvm/java-7-oracle/jre/bin/java
Priority: 1072
Slaves:
 java.1.gz /usr/lib/jvm/java-7-oracle/man/man1/java.1.gz[/INDENT]

So, the good news is that it works now.

---

### Post by oldos2er on 2013-11-26
Moved to Other OS/Distro Support.

---

