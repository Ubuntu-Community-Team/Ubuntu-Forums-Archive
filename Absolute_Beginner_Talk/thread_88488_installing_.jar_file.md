---
title: "installing .jar file"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by avenger on 2005-11-10
hi, i recently downloaded jedit, and tried to install it with the command 
java -jar jedit42install.jar.jar

the following error occured

teo@ubuntu:/media/linux/download$ java -jar jedit42install.jar.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.EventQueue.invokeLater(java.lang.Runnable) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.SwingUtilities.invokeLater(java.lang.Runnable) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.RepaintManager.addInvalidComponent(javax.swing.JComponent) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JComponent.revalidate() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JComponent.setOpaque(boolean) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JPanel.JPanel(java.awt.LayoutManager, boolean) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JPanel.JPanel() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.createGlassPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.getGlassPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.JRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.createRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.getRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.frameInit() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.JFrame() (/usr/lib/libgcj.so.6.0.0)
   at installer.SwingInstall.SwingInstall() (Unknown Source)
   at installer.Install.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:jedit42install.jar.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...18 more

did i do something wrong? i downloaded the file a few times, so i guess it shouldnt be a corrupted file.

---

### Post by timetunnel on 2005-11-10
[QUOTE=avenger]
java -jar jedit42install.jar.jar
[/QUOTE]
Rename that file to "jedit42install.jar" and see what happens. For a reason I don't know java doesn't seem to like the double ".jar.jar" as a file extensions - though I don't get the error messages you get (I'm using Sun's Java). 

Jens

---

### Post by avenger on 2005-11-10
hi tried that, didn't work though
after doing some googling, i think it might work if i could change my java path to sun's jdk
how do i go about doing that?

---

### Post by timetunnel on 2005-11-10
First, install Sun's Java following this tutorial:

[https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

After you have installed that java package you have to tell ubuntu that it shall be the default by following the instructions in chapter "Selecting the default Java version"

Jens

---

### Post by avenger on 2005-11-10
hi, thanks for the reply. i realised that sun's java wasnt in the option list. could it have something to do with me installing sun's jdk in a mounted partition?

---

### Post by timetunnel on 2005-11-10
[QUOTE=avenger]i realised that sun's java wasnt in the option list. could it have something to do with me installing sun's jdk in a mounted partition?[/QUOTE]

Did you install Sun's Java the way described in the tutorial I posted before? Because if not (and you used the installer from Sun directly) I think that's the reason it didn't show up in the option list (but I'm not sure here).
I don't understand the second part of your answer: a partition always has to be mounted to put files or install something there. What did you mean exactly?

Jens

---

### Post by avenger on 2005-11-10
i used the installer from sun directly actually. well i tried running this command
/media/linux/download$ sudo /media/linux/jdk1.5.0_05/bin/java jedit42install.jar
the ouput was:
sudo: unable to execute /media/linux/jdk1.5.0_05/bin/java: Permission denied

/media/linux/ is where i installed my jdk
i used chmod to set the permissions for the /media/linux to 777(everyone can read,write,execute any files in that folder) so i'm wondering what else could be denying the permission

---

### Post by timetunnel on 2005-11-10
No idea why that's happening, but I strongly recommend to uninstall the Java that you installed with Sun's installer  and use the tutorial I posted before. It's quite easy and after that jEdit (and all other Java applications) work without problems. And then you won't have any permission problems as well.

---

