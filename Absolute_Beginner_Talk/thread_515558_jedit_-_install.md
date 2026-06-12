---
title: "jedit - install"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Meloun on 2007-08-02
i installed jedit, at first java version..than i saw tha package deb..
so i deleted java version and install package deb...

and now in terminal.. 

>jedit

>Unable to access jarfile /home/meloun/jedit/4.2/jedit.jar

sudo /usr/bin/jedit is OK

---

### Post by apswartz on 2007-08-03
They are both the same java program requiring java to run. It is possible that the debian package wasn't completely compatible with ubuntu. I would reinstall it using the java-based installer again since that worked for you. You will end up with the exact same program.

---

### Post by Mongoose.wa on 2007-09-28
I installed Jedit by adding the Debian packages to my sources list and apt-get. It doesn't seem to want to run, however.

Here's what I get when I run "jedit" in terminal:

```
evan@evanlaptop:~$ jedit
[error] main: Exception in thread "main" 
[error] main: java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
[error] main:    at java.awt.Toolkit.
[error] main: getDefaultToolkit(libgcj.so.70)
[error] main:    at java.awt.Font.tk(libgcj.so.70)
[error] main:    at java.awt.Font.getPeerFrom
[error] main: Toolkit(libgcj.so.70)
[error] main:    at java.awt.Font.<init>(libgcj.so.70)
[error] main:    at org.gjt.sp.jedit.gui.SplashScre
[error] main: en.<init>(SplashScreen.java:37)
[error] main:    at org.gjt.sp.jedit.GUIUtilities.showSplashScreen(GUIUtilities.ja
[error] main: va:1519)
[error] main:    at org.gjt.sp.jedit.jEdit.main(jEdit.java:299)
[error] main: Caused by: java.lang.UnsatisfiedLinkError
[error] main: : libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
[error] main:    at java.la
[error] main: ng.Runtime._load(libgcj.so.70)
[error] main:    at java.lang.Runtime.loadLibrary(libgcj.so.70)
[error] main:    at java.lang.Sys
[error] main: tem.loadLibrary(libgcj.so.70)
[error] main:    at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
[error] main:    at ja
[error] main: va.lang.Class.initializeClass(libgcj.so.70)
[error] main:    at java.lang.Class.forName(libgcj.so.70)
[error] main:    at java.a
[error] main: wt.Toolkit.getDefaultToolkit(libgcj.so.70)
[error] main:    ...6 more
```

I'm guessing the problem is that I don't have the proper Java stuff installed, or something to that effect. I got the package java-common, but what else do I need?

---

### Post by lestel on 2008-03-10
Hi

I had the same problem. You should install java-6 in order to run your jedit. This is a link from jedit.org with an explanation and the steps to install java-6. It worked to me.

Regards

---

### Post by lestel on 2008-03-10
This is the link: [http://www.jedit.org/index.php?page=compatibility](http://www.jedit.org/index.php?page=compatibility) 

Sorry,


> **lestel said:**
> Hi

I had the same problem. You should install java-6 in order to run your jedit. This is a link from jedit.org with an explanation and the steps to install java-6. It worked to me.

Regards

---

