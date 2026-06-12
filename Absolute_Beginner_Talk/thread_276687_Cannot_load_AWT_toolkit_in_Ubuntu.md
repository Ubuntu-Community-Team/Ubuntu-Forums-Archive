---
title: "Cannot load AWT toolkit in Ubuntu"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2006-10-13
When I tried to run freedom.jar in Ubuntu 5.10, I got this error:-

```
smith@ubuntu:~/Desktop/YF$ java -jar freedom.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.tk() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.getPeerFromToolkit(java.lang.String, java.util.Map) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.Font(java.lang.String, int, int) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.FontUIResource.FontUIResource(java.lang.String, int, int) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.MetalLookAndFeel.MetalLookAndFeel() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.UIManager.<clinit>() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at emsgui.setLAF() (Unknown Source)
   at emsgui.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:freedom.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...14 more
```

How can I remove this error?

---

### Post by smith.norton on 2006-10-13
Please help. :(

How do I install those missing packages? Or are they present in some jar file and I simply need to add them in the CLASSPATH?

---

### Post by steve.horsley on 2006-10-13
I suggest that you install Sun's java VM. It's in the Multiverse repositories in Synaptic : package sun-java5-jre.

---

### Post by andykrueger on 2006-11-09
I encountered the same error as the original poster, when trying to run a different program.  I installed Sun's java VM as recommended, but I still receive the same error.  Also, I do know that I have Java installed and working correctly, so does anyone have an idea what else might fix this problem?

---

### Post by Fritti on 2006-11-26
Got the same error also. To fix it, install SUN java and then run the following command from a terminal:

$ sudo update-java-alternatives --jre --set java-1.5.0-sun

(enter your password when prompted)

---

### Post by flapane on 2006-12-07
flapane@a64:~$ sudo update-java-alternatives --jre --set java-1.5.0-sun
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-1.5.0-sun
flapane@a64:~$        

I have the same error and I've just installed java1.5.0.9 from java.com (32bit version for using firefox plugin)

---

### Post by nero666 on 2007-05-07
search for libgcj dev at synaptic
install it
restart eclipse
and be happy

---

### Post by EnkiduinNZ on 2008-03-01
> **Fritti said:**
> Got the same error also. To fix it, install SUN java and then run the following command from a terminal:

$ sudo update-java-alternatives --jre --set java-1.5.0-sun

(enter your password when prompted)

Won't that just set the Java Runtime Environment? Eclipse will need the SDK. Do you need to drop the --jre from that command?

Cheers,

Cliff

---

