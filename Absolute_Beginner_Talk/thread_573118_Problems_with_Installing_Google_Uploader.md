---
title: "Problems with Installing Google Uploader"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by Kem Rixen on 2007-10-11
After downloading google uploader, I wasn't entirely sure what to do, so I searched the forums and got this command to run:

```
java -cp /pathtofile/GoogleVideoUploader.jar com.google.uploader.Uploader *
```

(Before I go any further, yes it is pointing to the file on my computer) However, when I attempt to run it I get this error.

```

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.EventQueue.isDispatchThread(libgcj.so.70)
   at java.awt.EventQueue.invokeAndWait(libgcj.so.70)
   at javax.swing.SwingUtilities.invokeAndWait(libgcj.so.70)
   at com.google.uploader.Uploader.main(Uploader.java:19)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...4 more

```

---

### Post by Kem Rixen on 2007-10-11
Hmmm, I'm not usually one to bump a thread, but, the lack of a response is making me wonder if I even posted this in the right area...

---

### Post by Kem Rixen on 2007-10-12
Alright, this is the last time I'm going to bump this. I'm a little disappointed, however, that nobody has responded, at all.

---

### Post by Discombobulated on 2007-11-09
I'm having a similar problem:

```
x@bunti:~$ java -cp Desktop/GoogleVideoUploader.jar com.google.uploader.Uploader
Exception during event dispatch:
java.lang.NullPointerException
   at java.awt.font.TextLayout.<init>(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GdkFontPeer$GdkFontMetrics.stringWidth(libgcj.so.81)
   at javax.swing.border.TitledBorder.layoutBorderWithTitle(libgcj.so.81)
   at javax.swing.border.TitledBorder.paintBorder(libgcj.so.81)
   at javax.swing.JComponent.paintBorder(libgcj.so.81)
   at javax.swing.JComponent.paint(libgcj.so.81)
   at javax.swing.JComponent.paintChildren(libgcj.so.81)
   at javax.swing.JComponent.paint(libgcj.so.81)
   at javax.swing.JComponent.paintChildren(libgcj.so.81)
   at javax.swing.JComponent.paint(libgcj.so.81)
   at javax.swing.JComponent.paintChildren(libgcj.so.81)
   at javax.swing.JComponent.paint(libgcj.so.81)
   at javax.swing.JComponent.paintChildren(libgcj.so.81)
   at javax.swing.JComponent.paint(libgcj.so.81)
   at javax.swing.JLayeredPane.paint(libgcj.so.81)
   at javax.swing.JComponent.paintChildren(libgcj.so.81)
   at javax.swing.JComponent.paintDoubleBuffered(libgcj.so.81)
   at java.awt.Container$GfxPaintVisitor.visit(libgcj.so.81)
   at java.awt.Container.visitChild(libgcj.so.81)
   at java.awt.Container.visitChildren(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkComponentPeer.paintComponent(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkComponentPeer.handleEvent(libgcj.so.81)
   at java.awt.Component.dispatchEventImpl(libgcj.so.81)
   at java.awt.Container.dispatchEventImpl(libgcj.so.81)
   at java.awt.Window.dispatchEventImpl(libgcj.so.81)
   at java.awt.Component.dispatchEvent(libgcj.so.81)
   at java.awt.EventQueue.dispatchEvent(libgcj.so.81)
   at java.awt.EventDispatchThread.run(libgcj.so.81)

```

The 'uploader' window opens, yet only has a 'login...' button in the middle of it.  The rest of the window is blank.

Any ideas, anyone?

---

### Post by Discombobulated on 2007-11-09
Gutsy 7.10 amd 64, by the way.

---

### Post by Kem Rixen on 2007-11-10
I was having tons of problems with java after upgrading to Gutsy, so I did a clean install, and now google uploader works for me. So, I really have no idea for why it didn't work when I tried originally (while using Fiesty). Unless you really need google uploader, I don't recommend doing the same.

---

