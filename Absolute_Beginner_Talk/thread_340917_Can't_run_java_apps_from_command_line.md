---
title: "Can't run java apps from command line"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by madcap_magician on 2007-01-17
I have Eclipse set up and it works correctly.  Now I'm trying to run a Java program from the command line.

If I just do `java <class>` I get an java.lang.NoClassDefFoundError exception.  From looking around this seems to be from a bad CLASSPATH variable.

But if I do `java -cp . <class>` I still get the same error.  I'm not sure why this is, everywhere I've read about this error has fixed it by specifying the class path.  Even if I use the full path to the class file with the -cp flag it still doesn't work.

Is there something else I'm missing?

According to Eclipse it is using the JRE in 
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/lib/rt.jar

I also have Blackdown installed which I know is different but I'm not sure if anything is set up different.

`which java` gives me /usr/bin/java 
which is a link to  /etc/alternatives/java 
which is a link to  /usr/lib/j2se/1.4/bin/java
which is a link to  ../jre/bin/java

Any advice would be appreciated.

---

### Post by taurus on 2007-01-17
```
java -version
```

---

### Post by madcap_magician on 2007-01-17
madcap@phoenix:~/code$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

---

