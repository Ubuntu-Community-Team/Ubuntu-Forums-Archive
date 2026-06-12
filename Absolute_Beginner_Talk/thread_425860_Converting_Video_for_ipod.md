---
title: "Converting Video for ipod"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Icemanyurt on 2007-04-28
Hey I am trying to use iriverter to convert video for my ipod, but I keep getting this error:
> 
!!! An unhandled exception occured: class java.lang.UnsatisfiedLinkError
--- iriverter 0.16
--- 
--- Settings:
--- 
--- 
!!! no swt-pi-gtk-3236 in java.library.path
!!! 
!!! java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
!!! java.lang.Runtime.loadLibrary0(Runtime.java:823)
!!! java.lang.System.loadLibrary(System.java:1030)
!!! org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
!!! org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
!!! org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
!!! org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:28)
!!! org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:666)
!!! 
Exception in thread "main" java.lang.NoClassDefFoundError: Could not initialize class org.eclipse.swt.widgets.Display
        at org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.jav


I am using Feisty...

---

### Post by deadgobby on 2007-04-28
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?action=fullsearch&context=180&value=ipod&titlesearch=Titles](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?action=fullsearch&context=180&value=ipod&titlesearch=Titles)

---

### Post by greenapple on 2007-04-28
Perhaps you can try [winavi ipod video converter]("http://www.winavi.com/en/psp-3gp-mp4/ipod-video-converter.htm") if you are working on windows system.

---

### Post by ikus060 on 2007-06-12
I guest after 3 month you found the solution. But for other who continue to search, take a look at this url : [http://iriverter.thestaticvoid.org/index.fcgi/ticket/25?format=rss](http://iriverter.thestaticvoid.org/index.fcgi/ticket/25?format=rss)

---

### Post by BrowneR on 2007-06-16
that website seems to be down at the moment but the problem can be solved by issuing the following commans:

```
sudo apt-get install libswt3.2-gtk-jni
```

then you just need to add the following line to the iriverter launch script. this can be done as follows:

```
sudo gedit /usr/bin/iriverter
```

then add the following so that it becomes the second line in the file

```
LD_LIBRARY_PATH="/usr/lib/jni"
```

the finished file should now look like this:

```

#!/bin/sh
LD_LIBRARY_PATH="/usr/lib/jni"
prefix=/usr
exec_prefix=${prefix}
java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib -classpath $CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt.jar org.thestaticvoid.iriverter.ConverterUI $*

```

now simply save and launch iriverter as normal.

---

### Post by reality_hunter on 2007-06-28
thanks Browner! it worked like a charm

---

### Post by robbie75 on 2008-05-11
Thank you Browner!
Your suggestion made iriverter working for me too on Hardy Heron! ;-)

---

