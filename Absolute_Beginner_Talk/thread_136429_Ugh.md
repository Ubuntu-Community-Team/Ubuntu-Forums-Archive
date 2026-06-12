---
title: "Ugh"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by OkydOky on 2006-02-25
Using Azureus, It asked me to update, and install, this SWT plugin. Silly thing is, it's called STW plugin for win32 >.<

I simply click on Download and started doing smething else, without really looking what exacly I was updating.

Now Azureus will not start :p

```
azureus
Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3139 in  java.library.path
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:7 5)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThrea d.java:58)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.ja va:109)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:143)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:158)

```


I tried Removing and reinstalling Azureus.
Removing using: sudo apt-get remove azureus

And reinstalling it (Using automatix)

But I still get the same thing.

My Guess is removing it did not remove the extra update files.
Where are they?

or.. is it something else?

---

### Post by taurus on 2006-02-25
Try remove the .Aruzeus from your home directory as well...

```

rm -rf ~/.Azureus

```

---

### Post by OkydOky on 2006-02-25
Worked.

Thank you

---

### Post by dslabuser on 2006-03-10
I seem to a victim of the same update.  Tried the solution and no luck. uninstalled and then ran the rm -rf ~/.Azureus command and reinstalled no luck.
Am I missing something tried do a complete removal in synaptic and then that command and reinstall still no luck.

---

### Post by meborc on 2006-03-10
are you sure the .Azureus folder is removed from your home folder? go to nautilus, hit ctrl+H and look for it... i have a hairy feeling that you still have it there ;)

---

### Post by Perfect Storm on 2006-03-10
Arnie stated that Azureus will break if you update it.

If you want the newest Azureus, do this:

download Azureus here: [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) Pick Linux version 2.4.0.0.


```

cd /to/the/folder/where/you/saved/azureus 
sudo tar jxvf Azureus_2.4.0.0_linux.tar.bz2 -C /opt/ 
sudo chown -R root:root /opt/azureus/ 
sudo gedit /usr/share/applications/Azureus.desktop

```

add:
> 
[Desktop Entry]
Name=Azureus
Comment=P2P Client
Exec=/opt/azureus/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Internet;


---

### Post by tivalat on 2007-10-25
I can't start azureus. Help me,plz!
     ```
Aborted (core dumped)
     
```

---

