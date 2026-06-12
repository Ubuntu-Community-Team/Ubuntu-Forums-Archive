---
title: "How to compile multiple .java files at once in Ubuntu"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-03-19
I was just wondering how to compile multiple .java files at once. I know that in order to compile one .java file all you need to do is type

javac filename.java

then

java filename


The problem is that I have 5 .java files and they are all inter-related. 

They are Testing.java, Menu.java, GroupOfStudents.java, Course.java, and Student.java

I would greatly appreciate if you could give any help. I know how to do this in C and C++ but not Java. 

I would appreciate any help.

Thanks 

:guitar:

---

### Post by nsleiman on 2007-03-19
i would suggest this:

javac *.java 

:)

---

### Post by jprb85 on 2007-03-19
what does *.java mean?

---

### Post by nsleiman on 2007-03-19
instead of compiling filename1.java, filenam2.java ... you can use the wildcard * to state any kind of files having the extension ending with .java

the * matches everything with no restrictions

---

### Post by bluezapper on 2007-03-19
you can also use [[COLOR="Red"]Ant[/COLOR]]("http://ant.apache.org/")  to do such tasks.

It is available in ubuntu repositories.

Apache Ant is a Java-based build tool. In theory, it is kind of like make, without make's wrinkles.

hope this helps,

bluezapper

---

