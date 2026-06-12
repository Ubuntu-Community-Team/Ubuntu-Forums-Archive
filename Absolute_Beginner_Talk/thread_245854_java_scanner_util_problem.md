---
title: "java scanner util problem"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by emprog on 2006-08-28
Here is my output from java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

When trying to compile some very simple java code which imports java.util.Scanner I get compile errors.

erick@wolf:~/programming/java$ javac *.java
test.java:1: cannot resolve symbol
symbol  : class Scanner
location: package util
import java.util.Scanner;
                 ^
test.java:5: cannot resolve symbol
symbol  : class Scanner
location: class test
                Scanner input = new Scanner(System.in);
                ^
test.java:5: cannot resolve symbol
symbol  : class Scanner
location: class test
                Scanner input = new Scanner(System.in);
                                    ^
3 errors

Any ideas? :/

---

### Post by emprog on 2006-08-28
I tried updating but still no luck. Here is the output from -version

erick@wolf:~/programming/java$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
erick@wolf:~/programming/java$

Here is what I have selected on update-alternatives

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
      3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*     4        /usr/lib/j2sdk1.5-sun/bin/java


I even tried installing eclipse: aptitude install eclipse, but this didn't help. I am taking my second java course in college and classes have begun today :/ Any ideas as to why I cannot use scanner? Everything else seems to work for now.

[EDIT] I finally got everything working. If anyone else has similar problems I went here [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) 
The last thing I tried was installing the blackdown java packages and then I ran update-alternatives one more time for both java and javac.

---

### Post by ape on 2006-08-28
what about the javac binary? What alternatives are available for that and which one are you currently actually using? ('which javac' can also be used to point this out).

---

### Post by ZephyrXero on 2006-09-22
I tried setting the official Sun JRE as the default (instructions can be found in [this thread](http://ubuntuforums.org/showthread.php?t=201378)), but I still can't get it to work either :(

---

