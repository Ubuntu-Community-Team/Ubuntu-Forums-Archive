---
title: "Azureus fails to start"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by LordCla on 2007-06-27
Hello all!
I have installed azureus via apt-get install azureus
When i try to start it from the Aplications_>Internet->azureus menu nothing happens.

when I tried from a terminal i got this

root@cpu:~# azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/lib/jni/libswt-pi-gtk-3236.so: /usr/lib/jni/libswt-pi-gtk-3236.so: wrong ELF class: ELFCLASS64
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:80)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:61)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
root@cpu:~# 



I have to mention that because i use a amd64 (I have a intel core 2 dou e6400 proc)version of ubuntu and I installed java 32-bit edition along witrh firefox32 in order to get the flash player to work .. 

Any sugestions welcome...

---

### Post by aeiah on 2007-06-27
well it seems to be going on about the language rather than anything else. what language is your ubuntu?

additionally, azureus is java, and you may have to install a 32bit azureus, but im not sure. do other people have success with azureus in 64bit?

ktorrent is pretty good, if you dont get anywhere. deluge is good too, but was a bit too unstable and buggy last time i checked.

---

### Post by paradoxni on 2007-06-27
i have had no end of problems with firefox / java / azureus when using 64bit ubuntu ( i have a core2duo) in the end I just formated and installed Ubuntu 32bit as it was much easier to locate drivers and working software. It runs like a dream. Perhaps in the future I will try 64bit again when more is available.

---

### Post by LordCla on 2007-06-27
I'll try to look for a 32 bit azureus or a 64 bit java...

---

