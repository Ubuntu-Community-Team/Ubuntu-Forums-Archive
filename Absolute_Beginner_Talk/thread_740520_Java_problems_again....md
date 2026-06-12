---
title: "Java problems again..."
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by sidewalkcynic on 2008-03-30
[email]root@circuit-circus:/home/sidewalkcynic/.oper[/email]a/cache4/Compendium# ./compendium.sh
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at javax.swing.SwingUtilities$OwnerFrame.<init>(libgcj.so.70)
   at javax.swing.SwingUtilities.getOwnerFrame(libgcj.so.70)
   at javax.swing.JDialog.<init>(libgcj.so.70)
   at javax.swing.JDialog.<init>(libgcj.so.70)
   at com.compendium.ui.dialogs.UIStartUp.<init>(UIStartUp.java:51)
   at com.compendium.ProjectCompendium.main(ProjectCompendium.java:69)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...10 more
[email]root@circuit-circus:/home/sidewalkcynic/.oper[/email]a/cache4/Compendium#

---

### Post by Hospadar on 2008-03-30
what application, what version of java, what are you trying to do?

---

### Post by sidewalkcynic on 2008-03-31
[QUOTE=Compendium Installation Instructions for Linux]Compendium is a Java application, so it requires a Java Runtime Environment (v1.5) to be installed before you can run it.

Once you have downloaded the relevant .tar file from the compendiuminstitute.org website, simply unpack it. 

You can run Compendium by navigating to the Compendium directory and typing: ./compendium.sh[/QUOTE]

I am using Java 1.6, because it is the only download I can find.

And, I am trying to run the application program; I have had no problem running it on MS Windows.

---

