---
title: "Thinkorswim install on AMD64 Dapper system"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by gusoceros on 2007-04-07
Hi all- Im not sure I know what Im looking at here- I dont understand the command line stuff well enough yet to get this- however- here is the goal- to get this thinkorswim app to work on my amd64 dapper system.

I believe it has something to do with my JVM and the app being a 32 bit thing- but not sure

You can find the thinkorswim app here: [http://www.thinkorswim.com/installer/install.html](http://www.thinkorswim.com/installer/install.html)

This is the error I get when I run: sh ./thinkorswim.sh

[INDENT]gus@ubuntu:~/Thinkorswim$ sh ./thinkorswim_installer.sh
No suitable Java Virtual Machine could be found on your system.
The version of the JVM must be at least 1.5.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /home/gus/.install4j
[/INDENT]

Any help and hand holding would be appreciated- this is an important app for me.

G

PS- this is my java environment- I need guidance here on what I should be running as well- thanks:

[indent]gus@ubuntu:~/Thinkorswim$ sudo update-alternatives --config java

There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+    1        /usr/lib/j2se/1.4/bin/java
      2        /usr/bin/gij-wrapper-4.0
      3        /usr/bin/gij-wrapper-4.1
      4        /usr/lib/jvm/java-gcj/jre/bin/java
      5        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
      6        /usr/lib/jvm/ia32-java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 6[/indent]

---

### Post by gusoceros on 2007-04-07
I got this to work by installing JRE 6 and removing the recommended file.  I was then able to install the thinkorswim app.

G

---

### Post by barnkim on 2007-07-16
Thank you. This also worked for me.

---

### Post by kstump on 2007-11-14
I am even more of a newbie than you are. I can't get the Java update to work!

I am on Ubuntu 7.04 and I've read that the root functions have been disabled in this distro. The first thing the Java 6.3 wants me to do is the SU command which wants a password that I don't have.  Is there another way to install this thing?

Ken

---

### Post by era_new on 2007-11-17
If you need to use the root account go to the "Users and Groups" screen under System->Administration and manually enter a password for the root account.

---

### Post by kstump on 2007-11-19
Thank you for the information. It worked but unfortunately it didn't solve my problem.  I still need to get rid of 1.6 and find/go back to 1.5 (which i still haven't figured out how to do)

---

### Post by zipper123 on 2007-11-25
I got it to work when I install BOTH Java 1.5 and 1.6

Still the new TOS software compliant that I need to use only 1.5 but it is ok so far.

---

### Post by aBitLater on 2008-06-28
here is a page that helped me fix my OpenSuse java issue with ThinkOrSwim (TOS) java complaint on startup.

[http://en.opensuse.org/Java/setDefaultJava]("http://en.opensuse.org/Java/setDefaultJava")

perhaps this helps with Ubuntu also

---

