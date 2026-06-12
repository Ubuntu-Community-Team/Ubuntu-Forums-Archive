---
title: "Azureus doesn't work"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by bchen8341 on 2008-04-06
Hi, I run an AMD64 machine with gutsy installed, and everytime I try to download a torrent with azureus, it freezes and stops responding. I've tried this with many different torrents and it always happens. Here's what happens when I run it in a terminal (from the beginning, until the point where I add a torrent for downloading):

~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'

(SWT:6705): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1
Exception in thread "main" java.lang.NoSuchFieldError: type
        at org.gudy.azureus2.ui.swt.URLTransfer.pickBestType(URLTransfer.java:309)
        at org.gudy.azureus2.ui.swt.views.MyTorrentsView$51.dropAccept(MyTorrentsView.java:1997)
        at org.eclipse.swt.dnd.DNDListener.handleEvent(DNDListener.java:71)
        at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
        at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1085)
        at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1109)
        at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1094)
        at org.eclipse.swt.widgets.Widget.notifyListeners(Widget.java:935)
        at org.eclipse.swt.dnd.DropTarget.drag_drop(DropTarget.java:388)
        at org.eclipse.swt.dnd.DropTarget.Drag_Drop(DropTarget.java:253)
        at org.eclipse.swt.internal.gtk.OS._gtk_main_do_event(Native Method)
        at org.eclipse.swt.internal.gtk.OS.gtk_main_do_event(OS.java:5291)
        at org.eclipse.swt.widgets.Display.eventProc(Display.java:1149)
        at org.eclipse.swt.internal.gtk.OS._g_main_context_iteration(Native Method)
        at org.eclipse.swt.internal.gtk.OS.g_main_context_iteration(OS.java:1437)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2854)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:134)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:68)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:105)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:80)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:180)

Anyone know what's wrong?

---

### Post by Crafty Kisses on 2008-04-06
Couple of questions, what version of Java do you have, and also have you tried another torrent client?

---

### Post by bchen8341 on 2008-04-06
I don't know, is there a way to check my version of Java? (Although, if I go to System - Preferences, there's a thing called "IcedTea Java Policy Tool, so maybe that's what it is)

I haven't tried any other torrent client yet. I guess I can give them a try, although I'd really like to use Azureus since it's the one I'm more familiar with.

---

### Post by cozmicharlie on 2008-04-07
You can check your version of java using this command:
```
sudo update-alternatives --config java
```

You need the Sun-java6-JRE 
If you have the iced tea version then uninstall it and install Sun-java6-jre

That should work for you.

---

### Post by Inxsible on 2008-04-07
Azureus tends to be memory intensive...or at least it was until I stopped using it.

You may want to try out other torrent clients like :

Deluge
KTorrent
QBittorrent
Transmission -- is wonderful because you can use it via command line as well (good if you want to download something on your home machine while you are at work ) ;)

There are a bunch of others as well.

---

### Post by bchen8341 on 2008-04-10
How do I use sun-java6-JRE? I installed it and selected it in the update-alternatives --config java thing, and it shows:

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.1
 +        3    /usr/lib/jvm/java-7-icedtea/jre/bin/java
*         4    /usr/lib/jvm/java-6-sun/jre/bin/java

But Azureus still doesn't work, and still gives me the same error.

Edit: I tried Deluge, and it works fine, so I guess it's not really important anymore whether Azureus works or not.

---

### Post by tango_ninja on 2008-04-10
> **bchen8341 said:**
> Hi, I run an AMD64 machine with gutsy installed, and everytime I try to download a torrent with azureus, it freezes and stops responding. I've tried this with many different torrents and it always happens. Here's what happens when I run it in a terminal (from the beginning, until the point where I add a torrent for downloading):


Anyone know what's wrong?

I used to swear by Azureus ... switched over to **deluge** months ago. Have you tried it? It uses python instead of slow/confusing java. Might be something you want to check out.

---

### Post by energy. on 2008-04-10
which port(s) is azureus set to use?

---

### Post by nickpaton on 2008-04-10
Realise that you're using Deluge which is a great program, but looking at the Azureus problem, and the versions of Java you have running, you actually have two versions running:

+ 3 /usr/lib/jvm/java-7-icedtea/jre/bin/java
* 4 /usr/lib/jvm/java-6-sun/jre/bin/java

At the begining of the lines above - * indicates the default version - I'm not sure what + means but guess that it is the latest version.  In any case the fact that it's showing both verions could be causing Az to not know which one to go for and is tripping up.

Go into Synaptic and remove java7 icedtea.

While you're there remove Azureus as well

Then via Synaptic install: 

```
sun-java6-fonts
azureus
```

See if that works for you.

I personally prefer Az over the others coz of its configurability

---

### Post by nickpaton on 2008-04-10
> **energy. said:**
> which port(s) is azureus set to use?

Unfortunately it's not a port problem.  Having Az shut down like this is a common problem which tends to be java related.

---

### Post by cozmicharlie on 2008-04-10
nickpaton is correct - you have to uninstall the iced tea version.  Even trying to select another version of java will not work.  

You can reinstall Azureus from Synaptic but some people still report having problems with the version in Synaptic and it is an older version.  But, if it works for you then great - use it.  However, If you want the newer 3.0.x version then the easiest way to install is to go to getdeb.net, download the Azurues deb file and use Gdebi (native on Ubuntu) to install (simply double click on the downloaded file and it will install).  Or, alternatively, this is a good tutorial ([http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus](http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus)).  If you don't like the Vuze interface, change it in tools>options>interface>start Display Azuerus ui chooser and select classical view (make sure you click advanced when it asks what level you are).  

As per the ports - I agree this is not a port problem.  But, FYI Azurues will use any port you want.  When you set it up it will assign a port but you can change it.  Go to tools>Nat Firewall test you can test to see if your port is open and change the port if needed.

Once you uninstall the Java Iced Tea you should not have any problems.

---

