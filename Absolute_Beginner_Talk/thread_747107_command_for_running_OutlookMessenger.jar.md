---
title: "command for running OutlookMessenger.jar"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by _cyber@bit on 2008-04-06
java -jar OutlookMessenger.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.81)
   at java.awt.Window.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at javax.swing.JFrame.<init>(libgcj.so.81)
   at editor.chat.<init>(chat.java:30)
   at mainPage.messenger.<clinit>(messenger.java:62)
   at java.lang.Class.initializeClass(libgcj.so.81)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...7 more


is there any solution.. then make a reply .

---

### Post by harrybazeegar on 2008-04-06
well this may be because of the GNU java that you get along with the distro....

try this:
1. get the self extracting JRE archive from sun's site
2. extract it
3. rename the created folder to jdk/
4. on a terminal change your directory to <path to jdk/> /bin
5. type "./java -jar <path to OutlookMessenger.jar"

---

### Post by harrybazeegar on 2008-04-06
btw is did you create this jar yourself or did you download it?

---

