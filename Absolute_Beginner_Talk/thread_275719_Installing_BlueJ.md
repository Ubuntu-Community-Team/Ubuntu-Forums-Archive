---
title: "Installing BlueJ"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by james.gornall on 2006-10-11
having problems installing bluej in ubuntu!

when i try n run the .jar file I get this

```
gornall@gornall-desktop:~/utils/jdk1.5.0_09/bin$ java -jar bluej-213.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.Font.tk(libgcj.so.7)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.7)
   at java.awt.Font.<init>(libgcj.so.7)
   at javax.swing.plaf.FontUIResource.<init>(libgcj.so.7)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.<init>(libgcj.so.7)
   at javax.swing.UIManager.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at javax.swing.UIManager.getUI(libgcj.so.7)
   at javax.swing.text.JTextComponent.updateUI(libgcj.so.7)
   at javax.swing.text.JTextComponent.<init>(libgcj.so.7)
   at javax.swing.JTextField.<init>(libgcj.so.7)
   at javax.swing.JTextField.<init>(libgcj.so.7)
   at Installer.<clinit>(Installer.java:95)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...19 more
gornall@gornall-desktop:~/utils/jdk1.5.0_09/bin$

```

any ideas?

---

### Post by james.gornall on 2006-10-11
nvm, problem solved ^^

---

### Post by szf on 2006-10-11
> **james.gornall said:**
> nvm, problem solved ^^

Did you have to use:

[FONT="Courier New"]$ sudo update-alternatives --config java[/FONT]

to use the Sun JVM, perhaps?

---

