---
title: "Ubuntu 12.10 + Java + Nexus 7"
date: 2012-12-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by taffypride on 2012-12-04
Hi guys,

I've decided to take the plunge on my Nexus 7 and boot Ubuntu 12.10 natively as I require the use of Java (Android doesn't support it).

Having a few problems actually getting Java setup and wanted a bit of help.

I have installed the Ubunutu-Restricted-Extras and OpenJDK-7-JRE, however Firefox does not recognise that Java is actually installed.

Any possible solutions please?

---

### Post by Ongytenes on 2013-06-19
> **taffypride said:**
> Hi guys,

I've decided to take the plunge on my Nexus 7 and boot Ubuntu 12.10 natively as I require the use of Java (Android doesn't support it).

Having a few problems actually getting Java setup and wanted a bit of help.

I have installed the Ubunutu-Restricted-Extras and OpenJDK-7-JRE, however Firefox does not recognise that Java is actually installed.

Any possible solutions please?


I don't have this tablet so I can't directly test or verify my suggestion  I had similar problem in the past on a desktop. After installing Java I had to go into the Firefox plugin directory and make a symlink pointing to the Java SO (Shared Object) file. After that I started up Firefox and it discovered Java and utilized it. I hope this works for you.  You can read more on this on the Java site at: [http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html](http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html)

---

