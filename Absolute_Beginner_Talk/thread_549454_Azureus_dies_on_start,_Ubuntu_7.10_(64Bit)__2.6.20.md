---
title: "Azureus dies on start, Ubuntu 7.10 (64Bit)  2.6.20-16-generic"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Anolis on 2007-09-12
Azureus produces this terminal output, no display window is ever opened

apt-getted

```
anolis@anolis-desktop:~$ azureus 
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
anolis@anolis-desktop:~$ 
```

---

### Post by thedarkwinter on 2007-09-13
Hi

It may be to do with the version of java you are using:

Try typing this in the shell / konsole:

```

sudo update-alternatives --config java

```

and then choosing a different version of java (you will probably have 2 or 3 to choose from). you can switch between them, hopefully one of them will work!

good luck!

cheers,
tdw

---

### Post by Anolis on 2007-09-13
i already did this, i selected the latest version 1.6 i think. In the error message it is whining about Wrong ELF class ELF64 blah blah.. 

i tried running azureus with "linux32 azureus" but that didn't work

I have all the 32bit compat libs installed also

---

### Post by onero on 2007-09-13
Eh, I think you have a different problem from what I had before, but just in case it helps somehow...

I used to have the problem of Azureus having the loading screen and then just closing. To fix it, I downloaded a new .jar file and replaced the Azureus2.jar file in my installation (was running version 2.5.0.4). Dunno if that'll help ^^

---

