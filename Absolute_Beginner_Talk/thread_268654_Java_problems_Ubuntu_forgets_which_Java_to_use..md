---
title: "Java problems: Ubuntu forgets which Java to use."
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-09-30
I'm not sure if this is a problem with Ubuntu itself or just eclipse, but when I start up eclipse to do some programming, it uses the wrong Java. When I look under the installed JRE's it only has java 1.4 listed when I should be using 1.5. I have to run a search to find the other ones (I have four versions installed total for some reason). Once I select the right one and save my settings it works fine, but the next time I start up the computer it seems to revert back to the old settings and forget those other Java versions are even there.

Also, here's what I get when I type java -version:
```
alex@Shigeru:~$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

```

---

### Post by lebski88 on 2006-10-01
You could remove the older versions of java if you aren't using them. Failing that try looking through some of the config files in the Eclipse install directory. The java path might be set in an XML file somewhere possibly.

---

