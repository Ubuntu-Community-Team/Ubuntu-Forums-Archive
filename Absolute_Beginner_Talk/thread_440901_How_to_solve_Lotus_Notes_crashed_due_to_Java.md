---
title: "How to solve Lotus Notes crashed due to Java"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by david_kt on 2007-05-12
I have been able to install Lotus Notes (6.5.4) on 5 computers without any problem. What I need to do is use wine version 0.9.19 for Lotus Notes installation, and then upgrade wine to latest release to solve some bugs. You could check [official wine wiki]("http://wiki.winehq.org/LotusNotes") if you have difficulty in installing and running Lotus Notes.

But, on the sixth computer, for some reasons it did not work. It crashed when I open inbox, either locally or from server. And below is the error code in terminal:

```
Unable to create a suitable default GraphicsConfiguration.  Try changing your Display Settings.
        at sun.awt.Win32GraphicsDevice.getDefaultPixID(Native Method)
        at sun.awt.Win32GraphicsDevice.getDefaultConfiguration(Win32GraphicsDevice.java:151)
        at sun.awt.windows.WToolkit.resetGC(WToolkit.java:110)
        at sun.awt.windows.WToolkit.<clinit>(WToolkit.java:100)
        at java.lang.Class.forName1(Native Method)
        at java.lang.Class.forName(Class.java:142)
        at java.awt.Toolkit$2.run(Toolkit.java:533)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:524)
        at sun.awt.GlobalCursorManager$CursorEvent.<init>(GlobalCursorManager.java:42)
        at sun.awt.GlobalCursorManager.<clinit>(GlobalCursorManager.java:79)
        at java.awt.Cursor.initIDs(Native Method)
        at java.awt.Cursor.<clinit>(Cursor.java:194)
        at java.awt.Window.<init>(Window.java:198)
        at java.awt.Window.<init>(Window.java:244)
        at java.awt.Frame.<init>(Frame.java:329)
        at java.awt.Frame.<init>(Frame.java:276)
        at COM.ibm.JEmpower.applet.Console.<init>(Console.java:39)
        at COM.ibm.JEmpower.applet.AppletGroup.init(AppletGroup.java:532)
        at COM.ibm.JEmpower.applet.JEmpower.main(JEmpower.java:111)
JVMXM004: JVM is performing abort shutdown sequence

```

Lotus Notes come with java, and looks like wine failed to run it properly. The solution is quite simple i.e. to replace it with latest java.

Download it from [this website]("http://www.java.com/en/download/manual.jsp") or from [this direct link]("http://javadl.sun.com/webapps/download/AutoDL?BundleId=11193").

Open terminal and install it:

```
wine jre-6u1-windows-i586-p-s.exe 
```

Open nautilus and copy bin and lib folders from ~/.wine/drive_c/Program Files/Java/jre1.6.0_11 folder to ~/.wine/drive_c/Program Files/lotus/notes/jvm folder.

After that, I can open inbox without any problem.

DK

---

