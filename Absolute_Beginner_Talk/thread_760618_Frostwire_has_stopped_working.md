---
title: "Frostwire has stopped working"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Abras on 2008-04-20
Hi, 
Frostwire worked fine on my Hardy Heron desktop until yesterday. It won't even open now. I did install a bunch of updates  Firday night (With the update manager and I didn't even bother looking at what it was updating), so it's possible that the updates are what messed it up. Anyways, here is the output when I type "frostwire" into the terminal:

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
	at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Server VM (build 1.6.0-b09, mixed mode)

---

### Post by zitbug on 2008-04-20
Hello!

sudo update-java-alternatives -s java-1.5.0-sun

and working

---

### Post by don762003 on 2008-04-22
Did it work? That did not work for me.I t says:   update-java-alternatives: directory does not exist: /usr/lib/jvm/java-1.5.0-sun
don@don-desktop:~$

---

### Post by don762003 on 2008-04-22
used sudo update-java-alternatives -s java-6-sun and it worked. maybe this will help.

---

### Post by Abras on 2008-05-02
> **don762003 said:**
> used sudo update-java-alternatives -s java-6-sun and it worked. maybe this will help.Yes it did. Thanks for the help.

---

### Post by aedwards on 2008-05-19
> **don762003 said:**
> used sudo update-java-alternatives -s java-6-sun and it worked. maybe this will help.
Thanks, worked for me too.

---

