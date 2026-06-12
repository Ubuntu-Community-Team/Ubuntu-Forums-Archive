---
title: "java and flash for opera or epiphany?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by MkfIbK7a on 2007-01-08
just wondering whether there are java and flash plugins for opera

---

### Post by Sef on 2007-01-23
> just wondering whether there are java and flash plugins for opera

Read this for [Java on Opera]("https://help.ubuntu.com/community/OperaBrowser"):

> Install Java

If you start Opera from the console you may see the following error message if java doesn't work correctly:

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.

To fix this, correct the Java path under Tools -> Preferences -> Advanced Tab -> Content -> Java options. It should look similar to this:

/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/

Your actual java runtime version could be different from this one. Changes will not take effect until the browser is restarted. Use [WWW] [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) to test your Java Virtual Machine (JVM). You need to have Java installed for this. See Java to find out how to do that.


For Epiphany, if you set up Firefox, epiphany should pick up Java.

> flash for opera or epiphany

Once you install flash it should work for both of them.

---

