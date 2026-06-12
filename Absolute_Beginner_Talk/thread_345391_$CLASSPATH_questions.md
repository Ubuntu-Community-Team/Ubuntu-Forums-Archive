---
title: "$CLASSPATH questions"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by bcs on 2007-01-24
Hello,
I am having some confusion about setting the classpath and just have some really basic questions.

1.  What is the difference between the $CLASSPATH variable and the $PATH variable

2.  $CLASSPATH should be set in ~/.bashrc?  (with command like  "export CLASSPATH=/class/path/here:/another/here"

3.  Finally, I'm trying to compile a java program and I want javac to look in directory ~/JDocs for other classes that need to be compiled with my program.  I added "~/JDocs" to my classpath (in ~/.bashrc), but javac still not finding the classes that are there.

Can anyone help?  Thanks!

---

### Post by ieee488 on 2007-01-24
As I understand it, CLASSPATH is used when you type **java *yourclass*** to run your program, and PATH is used for locating the javac binary and also for the Java Runtime Engine.

I just went through this exercise on Windows 2000 yesterday.

Someone please correct me, if I am wrong.

---

