---
title: "java-gnome: bug?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by slamdunk on 2007-05-01
Hi,

running a sample application of java-gnome by eclipse I get this error:

Exception in thread "main" java.lang.UnsatisfiedLinkError: no glibjni-0.4 in java.library.path
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at org.gnu.glib.Struct.<clinit>(Struct.java:85)
	at demo.Main.main(Main.java:47)

at this row:

public static void main(String[] args) {
		// First call Gnome.init to initialize everything
        Program prog = Program.initGnome("GladeTest", "0.1", args);

obviously I have added various jars in classpath like gtk, gnome, glib, ecc

and so it seems  a bug of jars dependencies or not?
Have you any idea?

Thanks,
Alex

---

### Post by steve.horsley on 2007-05-01
It looks to me as though you are using the GNU implementation of java. I don't know if this is complete enough to be able to do JNI type stuff (and it looks like it isn't). I woud suggest that you install the sun jdk (varsion 5 and 6 are both in the repositories, I think).

---

### Post by slamdunk on 2007-05-01
# update-alternatives --config java

Ci sono 3 alternative che forniscono `java'.

  Selezione    Alternativa
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-wrapper-4.1
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java

Premi invio per mantenere il default[*], o inserisci il numero da selezionare:


and so I think that I'm using sun-sdk. But maybe eclipse is using "3"???

---

### Post by tageiru on 2007-05-01
> **steve.horsley said:**
> It looks to me as though you are using the GNU implementation of java. I don't know if this is complete enough to be able to do JNI type stuff (and it looks like it isn't). I woud suggest that you install the sun jdk (varsion 5 and 6 are both in the repositories, I think).

:roll: 

The problem is that /usr/lib/jni isn't found by the linker. The GNU implementation will work fine if you set LD_LIBRARY_PATH to /usr/lib/jni.

---

### Post by slamdunk on 2007-05-01
$ export LD_LIBRARY_PATH=/usr/lib/jni/

Thanks, it worked!

a question: but eclipse is using sun-sdk or gnu-java?

---

### Post by lmteijon on 2007-12-01
I tried to do that, I mean:   export LD_LIBRARY_PATH=/usr/lib/jni/ 
but it didn't work.  I'm using Ubuntu7.04 and NetBeans5.5

Did I miss something?

The code error follows below:

Exception in thread "main" java.lang.UnsatisfiedLinkError: no glibjni-0.4 in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:992)
        at org.gnu.glib.Struct.<clinit>(Struct.java:85)
Java Result: 1

---

### Post by lmteijon on 2007-12-02
Should I do that in a different way if I'm using NetBeans instead of Eclipse?
I mean:     $ export LD_LIBRARY_PATH=/usr/lib/jni/
It didn't work for me.

---

### Post by blazerw on 2008-02-20
I added the following to the arguments for the run profile in Eclipse:
```
-Djava.library.path=/usr/lib/jni
```

The place to put that is in the "Run" menu, the "Run..." choice, the "Arguments" tab.
Also, I linked:
```
/usr/lib/libglibjni-0.4.so -> /usr/lib/jni/libglibjni-0.4.so
```
And in /usr/lib/jni, I linked the following:
```
gtkjni-2.10.so -> libgtkjni-2.10.so
gtkjni.so -> libgtkjni-2.10.so
swt-gtk-3236.so -> /usr/lib/jni/libswt-gtk-3236.so
```

Do each part above and retry. First, add the argument. Try. Then just link the first one, Try. Then link the next one. Try. Etc.  I think only on link is required and it may not be if the argument above is correct.

I think that only the argument and the first link are required and that the other two links are holdovers from trial and error attempts. I didn't go back and cleanup after getting it to work.

Note, once the above is done, you should be able to run the application from within Eclipse.

---

