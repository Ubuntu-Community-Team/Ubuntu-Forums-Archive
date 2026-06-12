---
title: "HOW-TO Install Frostwire 4.13.1"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by motorhead on 2006-11-23
Hi all,
here's how i installed frostwire 4.13.1.

its new awesome features, that i know, are: new logo and torrents support. ok, here we go:

1. Remove frostwire
```

sudo apt-get remove frostwire

```

2. we download it and install it:)
```

wget http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb
sudo dpkg -i frostwire-4.13.1.i586.deb

```

3. ok, now, we install jre1.5 (no matter if it is already installed)
       download link: [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)
 next we copy the new file to /usr/java, if the directory does not exist, create it.
NOTE: this is the second file on the list: Linux (self-extracting file)(filesize: 16.27 MB)
```

sudo mkdir /usr/java
sudo cp jre-1_5_0_11-linux-i586.bin /usr/java

```

ok,now
```

sudo chmod a+x /usr/java/jre-1_5_0_11-linux-i586.bin
sudo /usr/java/jre-1_5_0_11-linux-i586.bin

```

type yes when it asks and you're done.

```

frostwire

```

Hope you can install it. :rolleyes:

---

### Post by jamesrose on 2006-11-23
This is in the wrong section.

Although,

its a very good HOWTO, I just downloaded & installed deb yesterday.

I will post a link to it when i get back. :D

---

### Post by motorhead on 2006-11-23
[QUOTE="jamesrose"]
This is in the wrong section.
[/QUOTE]
Sorry, i just saw "Absolute Beginner Talk" and i thought: "yeah, that's me".
[QUOTE="jamesrose"]
Although,

its a very good HOWTO, I just downloaded & installed deb yesterday.

I will post a link to it when i get back. 
[/QUOTE]
Thanks ^^

---

### Post by DarkDancer on 2006-11-26
Nice. Works brilliantly... ;)

---

### Post by msak007 on 2006-11-26
Thanks, didn't even know there was a new version coming out. It's not posted anywhere but their forums and on the developer blog - you'd think they would post it on the main page. Anyway...just tried to install it, and when I launch it all I get is a title bar, a blank screen, and a tray icon. I installed Java and the 09 update and it still won't work. I tried running update-alternatives and pointed it to the updated version to provide Java and still nothing. This is the output from the terminal when I run it:

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_09]
Configuring environment...
Loading FrostWire:
java.lang.ClassNotFoundException: irc.plugin.
        at java.net.URLClassLoader$1.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(Unknown Source)
        at java.lang.ClassLoader.loadClass(Unknown Source)
        at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
        at java.lang.ClassLoader.loadClass(Unknown Source)
        at java.lang.ClassLoader.loadClassInternal(Unknown Source)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Unknown Source)
        at irc.IRCApplication.loadPlugin(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:208)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:311)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:255)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@2006a0
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Unknown Source)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.enter(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.addStatus(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.statusCreated(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.sourceCreated(Unknown Source)
        at irc.IRCApplication.sourceCreated(Unknown Source)
        at irc.IRCServer.enumerateSourcesAsCreated(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:208)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:311)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:255)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@2006a0
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Unknown Source)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.activate(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.enter(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.addStatus(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.statusCreated(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.sourceCreated(Unknown Source)
        at irc.IRCApplication.sourceCreated(Unknown Source)
        at irc.IRCServer.enumerateSourcesAsCreated(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:208)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:311)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:255)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@2006a0
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Unknown Source)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:208)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:311)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:255)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@2006a0
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Unknown Source)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:208)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:311)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:255)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@2006a0
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Unknown Source)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:208)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:311)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:255)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
TRAY_TOOLTIP:::FrostWire
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@2006a0
current thread is Thread[AWT-EventQueue-0,7,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Unknown Source)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.disconnect(Unknown Source)
        at irc.IRCInterpretor.handleCommand(Unknown Source)
        at irc.RootInterpretor.sendString(Unknown Source)
        at irc.Source.sendString(Unknown Source)
        at irc.IRCApplication.sendString(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.disconnect(ChatMediator.java:132)
        at com.limegroup.gnutella.gui.GUIMediator.close(GUIMediator.java:994)
        at com.limegroup.gnutella.gui.MainFrame$3.windowClosing(MainFrame.java:257)
        at java.awt.AWTEventMulticaster.windowClosing(Unknown Source)
        at java.awt.AWTEventMulticaster.windowClosing(Unknown Source)
        at java.awt.AWTEventMulticaster.windowClosing(Unknown Source)
        at java.awt.Window.processWindowEvent(Unknown Source)
        at javax.swing.JFrame.processWindowEvent(Unknown Source)
        at java.awt.Window.processEvent(Unknown Source)
        at java.awt.Component.dispatchEventImpl(Unknown Source)
        at java.awt.Container.dispatchEventImpl(Unknown Source)
        at java.awt.Window.dispatchEventImpl(Unknown Source)
        at java.awt.Component.dispatchEvent(Unknown Source)
        at java.awt.EventQueue.dispatchEvent(Unknown Source)
        at java.awt.EventDispatchThread.pumpOneEventForHierarchy(Unknown Source)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
        at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
        at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
        at java.awt.EventDispatchThread.run(Unknown Source)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@2006a0
current thread is Thread[AWT-EventQueue-0,7,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Unknown Source)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.disconnect(Unknown Source)
        at irc.IRCInterpretor.handleCommand(Unknown Source)
        at irc.RootInterpretor.sendString(Unknown Source)
        at irc.Source.sendString(Unknown Source)
        at irc.IRCApplication.sendString(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.disconnect(ChatMediator.java:132)
        at com.limegroup.gnutella.gui.GUIMediator.close(GUIMediator.java:994)
        at com.limegroup.gnutella.gui.MainFrame$3.windowClosing(MainFrame.java:257)
        at java.awt.AWTEventMulticaster.windowClosing(Unknown Source)
        at java.awt.AWTEventMulticaster.windowClosing(Unknown Source)
        at java.awt.AWTEventMulticaster.windowClosing(Unknown Source)
        at java.awt.Window.processWindowEvent(Unknown Source)
        at javax.swing.JFrame.processWindowEvent(Unknown Source)
        at java.awt.Window.processEvent(Unknown Source)
        at java.awt.Component.dispatchEventImpl(Unknown Source)
        at java.awt.Container.dispatchEventImpl(Unknown Source)
        at java.awt.Window.dispatchEventImpl(Unknown Source)
        at java.awt.Component.dispatchEvent(Unknown Source)
        at java.awt.EventQueue.dispatchEvent(Unknown Source)
        at java.awt.EventDispatchThread.pumpOneEventForHierarchy(Unknown Source)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
        at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
        at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
        at java.awt.EventDispatchThread.run(Unknown Source)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@2006a0
current thread is Thread[AWT-EventQueue-0,7,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Unknown Source)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.disconnect(Unknown Source)
        at irc.IRCInterpretor.handleCommand(Unknown Source)
        at irc.RootInterpretor.sendString(Unknown Source)
        at irc.Source.sendString(Unknown Source)
        at irc.IRCApplication.sendString(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.disconnect(ChatMediator.java:132)
        at com.limegroup.gnutella.gui.GUIMediator.close(GUIMediator.java:994)
        at com.limegroup.gnutella.gui.MainFrame$3.windowClosing(MainFrame.java:257)
        at java.awt.AWTEventMulticaster.windowClosing(Unknown Source)
        at java.awt.AWTEventMulticaster.windowClosing(Unknown Source)
        at java.awt.AWTEventMulticaster.windowClosing(Unknown Source)
        at java.awt.Window.processWindowEvent(Unknown Source)
        at javax.swing.JFrame.processWindowEvent(Unknown Source)
        at java.awt.Window.processEvent(Unknown Source)
        at java.awt.Component.dispatchEventImpl(Unknown Source)
        at java.awt.Container.dispatchEventImpl(Unknown Source)
        at java.awt.Window.dispatchEventImpl(Unknown Source)
        at java.awt.Component.dispatchEvent(Unknown Source)
        at java.awt.EventQueue.dispatchEvent(Unknown Source)
        at java.awt.EventDispatchThread.pumpOneEventForHierarchy(Unknown Source)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
        at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
        at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
        at java.awt.EventDispatchThread.run(Unknown Source)

```

---

### Post by Cardmaster91 on 2006-11-26
how do u create a folder in usr? thhe text is gray and unclickable

---

### Post by ThrobbingBrain66 on 2006-11-26
> **msak007 said:**
> Thanks, didn't even know there was a new version coming out. It's not posted anywhere but their forums and on the developer blog - you'd think they would post it on the main page. Anyway...just tried to install it, and when I launch it all I get is a title bar, a blank screen, and a tray icon. I installed Java and the 09 update and it still won't work. I tried running update-alternatives and pointed it to the updated version to provide Java and still nothing. This is the output from the terminal when I run it:

It's not posted anywhere because (according to the forums) its a pre-beta..read alpha :)  They won't put it on the front page until its a beta, and maybe not until its RC/Final.

---

### Post by ThrobbingBrain66 on 2006-11-26
> **Cardmaster91 said:**
> how do u create a folder in usr? thhe text is gray and unclickable

you have to be root to make a folder.  so hit alt+F2 and type 
```
gksu nautilus
```

navigate to usr and THEN make your folder

---

### Post by gubatron on 2006-11-27
> its new awesome features, that i know, are: new logo and torrents support. 

It also connects to 4 ultrapeers, which broadens the search result horizon, it acts exactly as LimeWire PRO, so you'll always be on a "Turbo Charged" connection, and might have less wait time on download queues.

For the guy having problems with irc.plugin, don't worry about it for now, this version is not including Chat for linux due to some nasty AWT bugs we need to ask for help to the PJIRC team.

Mac Users (if you end up here by anychance), you can however use the chat features, no AWT bugs there.

---

### Post by Steve S. on 2006-12-17
Nice how-to...worked fine with Edgy.  Thanks!

---

### Post by msak007 on 2006-12-17
The problem I had with the blank screen was due to XGL / Beryl (guess there's a bug in Java / XGL / Beryl). The only problem I have now is there's no System Tray icon. I installed the beta deb from Frostwire's web site.

---

### Post by motorhead on 2006-12-22
if any of you had problems installing the java package it was beacause there's a new version of JRE. I've updated my post and now it should work without any problem.

---

### Post by OsakaWilson on 2006-12-25
This worked great! I had a connection problem ever since I upgraded to Edgy, but this connected fine.

The problem is that when I put in Japanese text, it produces garbage characters. Japanese input worked fine with previous versions of Frostwire. Is there a way to fix this?

---

### Post by Jorge32 on 2006-12-25
I have a problem, I made it all how it said, but this message appears:
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
ls: /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)


what do I need to do?

---

### Post by mahiyar on 2006-12-26
jorge 32 -- I had the same problem here. By some strange reason it seems that when executing the java bin file, the installation is in some other directory. What I did was -- I did not execute the java bin file from the CLI, but opened nautilus as root (sudo nautilus) from CLI and then on double clicking the bin file ..... voila the java folder was in the /usr/java/, and everything was pefect. And I should tell u installing frost wire was worth all the effort. (wonder why i have ever used limewire in the windows day). Please do not ask me what effect the other dud installation of java will have.

---

### Post by mahiyar on 2006-12-26
What a silly *** am I. Well the java folder got installed in my home directory from where I was executing the bin file. So u need to cd to your /usr/java folder and execute the bin file.

---

### Post by Jorge32 on 2006-12-26
thanks mahiyar!
 I've manually moved it into the /usr/java folder and now I am able to open the program.

---

### Post by electrodad on 2007-01-06
> **motorhead said:**
> Hi all,
here's how i installed frostwire 4.13.1.

its new awesome features, that i know, are: new logo and torrents support. ok, here we go:

1. Remove frostwire
```

sudo apt-get remove frostwire

```

2. we download it and install it:)
```

wget http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb
sudo dpkg -i frostwire-4.13.1.i586.deb

```

3. ok, now, we install jre1.5 (no matter if it is already installed)
       download link: [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)
 next we copy the new file to /usr/java, if the directory does not exist, create it.
NOTE: this is the second file on the list: Linux (self-extracting file)(filesize: 16.27 MB)
```

sudo mkdir /usr/java
sudo cp jre-1_5_0_10-linux-i586.bin /usr/java

```

ok,now
```

sudo chmod a+x /usr/java/jre-1_5_0_10-linux-i586.bin
sudo /usr/java/jre-1_5_0_10-linux-i586.bin

```

type yes when it asks and you're done.

```

frostwire

```

Hope you can install it. :rolleyes:

I followed your instructions as best my nOOb self could but when I typed frostwire it told my java was too old and please load current version.](*,) I would like to get this working. What could I have do wrong?

---

### Post by Perfect Storm on 2007-01-06
```
sudo update-alternatives --config java
```

---

### Post by electrodad on 2007-01-06
> **Artificial Intelligence said:**
> ```
sudo update-alternatives --config java
```


This is what's happening when I type frostwire:

electrodad@electrodad-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
electrodad@electrodad-laptop:~$                                       

:confused: 
Any help would be appreciated

---

### Post by stk47rr on 2007-01-16
> **motorhead said:**
> Hi all,
here's how i installed frostwire 4.13.1.

its new awesome features, that i know, are: new logo and torrents support. ok, here we go:

1. Remove frostwire
```

sudo apt-get remove frostwire

```

2. we download it and install it:)
```

wget http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb
sudo dpkg -i frostwire-4.13.1.i586.deb

```

3. ok, now, we install jre1.5 (no matter if it is already installed)
       download link: [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)
 next we copy the new file to /usr/java, if the directory does not exist, create it.
NOTE: this is the second file on the list: Linux (self-extracting file)(filesize: 16.27 MB)
```

sudo mkdir /usr/java
sudo cp jre-1_5_0_10-linux-i586.bin /usr/java

```

ok,now
```

sudo chmod a+x /usr/java/jre-1_5_0_10-linux-i586.bin
sudo /usr/java/jre-1_5_0_10-linux-i586.bin

```

type yes when it asks and you're done.

```

frostwire

```

Hope you can install it. :rolleyes:

i did all of this and once i type frostwire it says bash: /usr/bin/frostwire: no such file or directory
i need help bad. i suck at this. 

 bash: /usr.bin/frostwire: no such fiei did all of this and once i type frostwire it says

please help.

---

### Post by stk47rr on 2007-01-16
i forgot to mention that i'm running the latest version of ubuntu and i'm also running beryl at start up. thanks again.

---

### Post by pay on 2007-01-16
Frostwire doesn't work properly with beryl... but that probably isn't the root of your problem

---

### Post by SSupport on 2007-01-21
Had some issues getting things working myself. I installed the .deb package, and it installed no problem- icon was in the Application panel....but when I clicked on the icon, it did nothing.

Found that going through Synaptic, and right-clicking on frostwire, it gives the option to "Mark Suggested for Installation"  the missing pieces of Java needed to run.  Once I downloaded the missing 5 files, it ran with no issues.  

Hope this helps other n3wbs like myself.  :D

---

### Post by dvarsam on 2007-01-21
Hello!

I have heard about spyware installed in "Limewire"...
And therefore I wanted to test whether "Frostwire" is behaving the same...

So, in order to test whether this could be true, I installed "frostwire".

_For those equipped with Routers_:

Have you noticed that right after the installation & while your Internet connection is idle (i.e. _all_ your Mozilla Firefox's windows are closed), your Router's traffic lights are blinking _continuously_?
I have heard about "spyware" being involved, but can somebody with good knowledge provide some explanation?

To verify this:

1. Before installing anything, my router's lights are OK (nothing is blinking unless I specifically surf the Net for something...).
2. I installed "frostwire" & required "j2re".
3. My Router's lights are _now_ blinking like crazy for 3 continuous seconds every 10 seconds, even though I have all my Mozilla Firefox's windows closed... 
4. I go ahead & **un-install** "frostwire".
5. Router keeps blinking like crazy for 3 continuous seconds every 10 seconds, even though I have _all_ my Mozilla Firefox's windows closed...
6. I then noticed that even though the "frostwire" program got removed, the icon in the Top Panel was still there... 
7. So, I right-clicked on the icon & selected "exit".
8. I think/hope after this, that everything is back to normal... (i.e. router should be fine...)

I guess that this is happening when the program is running...
But even if you close the program (but it's icon remains in the Top Panel), unless you close that too, the Router shows traffic...
Why does this happen?
Could it be "spyware" related?

Thanks.

P.S.> I guess that I have "spyware" related issues/fears since the Windows use/era... :)
Please check this out & respond...

---

### Post by sniper85 on 2007-01-22
I get a Fatal Error whenever I try to run Frostwire

```

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
[Fatal Error] :2:108: Content is not allowed in trailing section.
CyberGarage warning : org.xml.sax.SAXParseException: Content is not allowed in trailing section.
org.cybergarage.xml.ParserException: org.xml.sax.SAXParseException: Content is not allowed in trailing section.
        at org.cybergarage.xml.parser.XercesParser.parse(XercesParser.java:122)
        at org.cybergarage.soap.SOAPRequest.postMessage(SOAPRequest.java:92)
        at org.cybergarage.upnp.control.ActionRequest.post(ActionRequest.java:137)
        at org.cybergarage.upnp.Action.postControlAction(Action.java:317)
        at com.limegroup.gnutella.UPnPManager.addMapping(UPnPManager.java:362)
        at com.limegroup.gnutella.UPnPManager.mapPort(UPnPManager.java:285)
        at com.limegroup.gnutella.Acceptor.init(Acceptor.java:261)
        at com.limegroup.gnutella.RouterService$Initializer.run(RouterService.java:377)
        at com.limegroup.gnutella.util.ThreadFactory*****run(ThreadFactory.java:18)
        at com.limegroup.gnutella.util.DefaultThreadPool$Processor.run(DefaultThreadPool.java:126)
        at java.lang.Thread.run(Thread.java:619)
Caused by: org.xml.sax.SAXParseException: Content is not allowed in trailing section.
        at com.sun.org.apache.xerces.internal.parsers.DOMParser.parse(DOMParser.java:239)
        at com.sun.org.apache.xerces.internal.jaxp.DocumentBuilderImpl.parse(DocumentBuilderImpl.java:283)
        at org.cybergarage.xml.parser.XercesParser.parse(XercesParser.java:108)
        ... 10 more
[Fatal Error] :2:108: Content is not allowed in trailing section.
CyberGarage warning : org.xml.sax.SAXParseException: Content is not allowed in trailing section.
org.cybergarage.xml.ParserException: org.xml.sax.SAXParseException: Content is not allowed in trailing section.
        at org.cybergarage.xml.parser.XercesParser.parse(XercesParser.java:122)
        at org.cybergarage.soap.SOAPRequest.postMessage(SOAPRequest.java:92)
        at org.cybergarage.upnp.control.ActionRequest.post(ActionRequest.java:137)
        at org.cybergarage.upnp.Action.postControlAction(Action.java:317)
        at com.limegroup.gnutella.UPnPManager.addMapping(UPnPManager.java:362)
        at com.limegroup.gnutella.UPnPManager.mapPort(UPnPManager.java:320)
        at com.limegroup.gnutella.Acceptor.init(Acceptor.java:261)
        at com.limegroup.gnutella.RouterService$Initializer.run(RouterService.java:377)
        at com.limegroup.gnutella.util.ThreadFactory*****run(ThreadFactory.java:18)
        at com.limegroup.gnutella.util.DefaultThreadPool$Processor.run(DefaultThreadPool.java:126)
        at java.lang.Thread.run(Thread.java:619)
Caused by: org.xml.sax.SAXParseException: Content is not allowed in trailing section.
        at com.sun.org.apache.xerces.internal.parsers.DOMParser.parse(DOMParser.java:239)
        at com.sun.org.apache.xerces.internal.jaxp.DocumentBuilderImpl.parse(DocumentBuilderImpl.java:283)
        at org.cybergarage.xml.parser.XercesParser.parse(XercesParser.java:108)
        ... 10 more
[Fatal Error] :2:473: Content is not allowed in trailing section.
CyberGarage warning : org.xml.sax.SAXParseException: Content is not allowed in trailing section.
org.cybergarage.xml.ParserException: org.xml.sax.SAXParseException: Content is not allowed in trailing section.
        at org.cybergarage.xml.parser.XercesParser.parse(XercesParser.java:122)
        at org.cybergarage.soap.SOAPRequest.postMessage(SOAPRequest.java:92)
        at org.cybergarage.upnp.control.ActionRequest.post(ActionRequest.java:137)
        at org.cybergarage.upnp.Action.postControlAction(Action.java:317)
        at com.limegroup.gnutella.UPnPManager$StaleCleaner.run(UPnPManager.java:527)
        at com.limegroup.gnutella.util.ThreadFactory*****run(ThreadFactory.java:18)
        at com.limegroup.gnutella.util.DefaultThreadPool$Processor.run(DefaultThreadPool.java:126)
        at java.lang.Thread.run(Thread.java:619)
Caused by: org.xml.sax.SAXParseException: Content is not allowed in trailing section.
        at com.sun.org.apache.xerces.internal.parsers.DOMParser.parse(DOMParser.java:239)
        at com.sun.org.apache.xerces.internal.jaxp.DocumentBuilderImpl.parse(DocumentBuilderImpl.java:283)
        at org.cybergarage.xml.parser.XercesParser.parse(XercesParser.java:108)
        ... 7 more
java.lang.ClassNotFoundException: irc.plugin.
        at java.net.URLClassLoader*****run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at irc.IRCApplication.loadPlugin(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@c06258
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.enter(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.addStatus(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.statusCreated(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.sourceCreated(Unknown Source)
        at irc.IRCApplication.sourceCreated(Unknown Source)
        at irc.IRCServer.enumerateSourcesAsCreated(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@c06258
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.activate(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.enter(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.addStatus(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.statusCreated(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.sourceCreated(Unknown Source)
        at irc.IRCApplication.sourceCreated(Unknown Source)
        at irc.IRCServer.enumerateSourcesAsCreated(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@c06258
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@c06258
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@c06258
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
TRAY_TOOLTIP:::FrostWire
Y LA IMAGEN ES >>>>>>>>>>>>>>>>>
frosticon
<<<<<<<<<<<<<<<<
Error: Couldn't find per display information

******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing) 

```

---

### Post by Lucho77 on 2007-01-24
Nice Job, It worked for me in the first try.
Thanks 'motorhead'

---

### Post by NeoLithium on 2007-01-30
Wow; I was using the old frostwire still; this one is FAR better; even for a beta!  Thanks for letting us know; I had no idea this version was kicking around.

---

### Post by OvrtheEdge on 2007-02-04
I am running Dapper 6.0.6 and when I run Frostwire I get this;

Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

I saw that Jorge32 and some others had the same problem .... Try this .... sudo apt-get install gtk-gnutella   ...... I did this and Frostwire worked fine on 6.10 but still cannot get it to work on 6.0.6.

---

### Post by cinnix on 2007-02-06
> **OvrtheEdge said:**
> I am running Dapper 6.0.6 and when I run Frostwire I get this;

Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

I saw that Jorge32 and some others had the same problem .... Try this .... sudo apt-get install gtk-gnutella   ...... I did this and Frostwire worked fine on 6.10 but still cannot get it to work on 6.0.6.

yea i just had the same problem in edgy, fresh install. 
```
java -version
```
came back as v1.4 eerily enough.

running this by in terminal got it working for me
```
sudo apt-get install sun-java5-jre sun-java5-plugin
```

---

### Post by ricardisimo on 2007-02-10
> **motorhead said:**
> Hi all,
here's how i installed frostwire 4.13.1.

its new awesome features, that i know, are: new logo and torrents support. ok, here we go:

1. Remove frostwire
```

sudo apt-get remove frostwire

```

2. we download it and install it:)
```

wget http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb
sudo dpkg -i frostwire-4.13.1.i586.deb

```

3. ok, now, we install jre1.5 (no matter if it is already installed)
       download link: [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)
 next we copy the new file to /usr/java, if the directory does not exist, create it.
NOTE: this is the second file on the list: Linux (self-extracting file)(filesize: 16.27 MB)
```

sudo mkdir /usr/java
sudo cp jre-1_5_0_10-linux-i586.bin /usr/java

```

ok,now
```

sudo chmod a+x /usr/java/jre-1_5_0_10-linux-i586.bin

This is as far as I get, then I get:
[CODE]chmod: cannot access `/usr/java//usr/java/jre-1_5_0_11-linux-i586.bin': No such file or directory

```
It's there, however. I put it there two different ways, just to see if that somehow made a difference. No dice. Any ideas?

---

### Post by phossal on 2007-02-10
> **ricardisimo said:**
> This is as far as I get, then I get: cannot access `***/usr/java/**/usr/java/jre-1_5_0_11-linux-i586.bin*': No such file or directory
It's there, however. I put it there two different ways, just to see if that somehow made a difference. No dice. Any ideas?
You shouldn't have /usr/java/ appearing twice. That's part of the problem.

---

### Post by ricardisimo on 2007-02-10
That's bizarre... my terminal's still open, and it doesn't have that doubled-up line anywhere. It's just like this:
```
~$ sudo chmod a+x /usr/java/jre-1_5_0_10-linux-i586.bin
chmod: cannot access `/usr/java/jre-1_5_0_10-linux-i586.bin': No such file or directory
```
Something odd happened while posting, 'cause that ain't the problem.

---

### Post by phossal on 2007-02-10
Are you sure it's not in /usr/***lib*** ? If you're going to install a .bin file anyway, why not grab JDK 6 right from SUN?

---

### Post by ricardisimo on 2007-02-10
phossal,
I read your tutorial (very nice, by the way) and you mention at one point that one could add the repos and run apt-get for it. I think I'll take that option, considering that compiling by hand almost never works for me, as this very thread can attest. What are the pertinent repositories, and would you by any chance know the line(s) to add in (I'm assuming) sources.list? Thanks.

---

### Post by phossal on 2007-02-10
The sun-java6-jdk is in the backports. My sources.list file looks something like this (courtesy of the wiki):
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen

```
For the record, you don't *compile* the .bin file from Java. It's almost as easy as extracting it. It creates a folder and you're up an running. Though you think you're avoiding some work by grabbing the package, you're not. You'll still end up configuring update-alternatives, the firefox plugin, JAVA_HOME, and javaws (Java Web Start). Plus, when you ask for help, it's significantly more difficult to diagnose problems with a failed (or half) package install.

---

### Post by ricardisimo on 2007-02-10
Oops! I just noticed what the problem was: the current .bin is "jre-1_5_0_**[COLOR="Blue"]11[/COLOR]**-linux-i586.bin", while the code calls for "jre-1_5_0_**[COLOR="Red"]10[/COLOR]**-linux-i586.bin". Sorry for the confusion. Hopefully the rest of the install will go swimmingly.

---

### Post by Brian Smith on 2007-02-19
> **Artificial Intelligence said:**
> ```
sudo update-alternatives --config java
```

Thanks, that worked great for me, I was able to select Java 1-5 instead of my previously chosen 1-4-2.

Frostwire was then able to start from CLI.

---

### Post by kamaboko on 2007-02-19
wow, i didn't go to any of that trouble.  i just clicked on the software link at frostwire and let gDebi install from there.  it was perfect.

---

### Post by starscalling on 2007-02-19
well 
1. java is now _11 instead of _10
2. frostwire gives me an error about configuring my username
3. no systray icon
using dapper

---

### Post by msak007 on 2007-02-20
> **starscalling said:**
> well 
1. java is now _11 instead of _10
2. frostwire gives me an error about configuring my username
3. no systray icon
using dapper
I have the same exact problems. I have the latest Java running and was able to install Frostwire and start it, but when configuring any options get an error that I have to choose a user name, and there is no System Tray icon.

---

### Post by motorhead on 2007-03-01
> **msak007 said:**
> I have the same exact problems. I have the latest Java running and was able to install Frostwire and start it, but when configuring any options get an error that I have to choose a user name, and there is no System Tray icon.

Same here.

---

### Post by phossal on 2007-03-02
How do you launch the program? And what options are you trying to configure?

---

### Post by krypto_wizard on 2007-03-03
Thank you. I got helped with this thread.

---

### Post by msak007 on 2007-03-03
> **phossal said:**
> How do you launch the program? 
Through the menu / Kicker icon as well as terminal. Regardless of the method, the result is the same. Here's some terminal output if you can make anything of it:
```

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
java.lang.ClassNotFoundException: irc.plugin.
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at irc.IRCApplication.loadPlugin(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@158291
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.enter(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.addStatus(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.statusCreated(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.sourceCreated(Unknown Source)
        at irc.IRCApplication.sourceCreated(Unknown Source)
        at irc.IRCServer.enumerateSourcesAsCreated(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@158291
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.activate(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.enter(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.addStatus(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.statusCreated(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.sourceCreated(Unknown Source)
        at irc.IRCApplication.sourceCreated(Unknown Source)
        at irc.IRCServer.enumerateSourcesAsCreated(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@158291
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@158291
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@158291
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
```> **phossal said:**
> And what options are you trying to configure? Anything. The minute you bring up the options window (Tools --> Options), then click "OK" (even if you haven't made any changes), you get 2 error boxes (attached screenshots).

Not sure if it's relevant, but I'm using Kubuntu Edgy. starscalling, are you using KDE or Gnome?

---

### Post by phossal on 2007-03-03
I really *can't* make anything out of it. I run from Java exceptions. ;) I haven't actually used a packaged version of Java for a long time, and I haven't used anything but the .tar.gz version of the *wires. Launching them has never really been an issue. You're not running something else that might impact them are you, like Beryl?

---

### Post by msak007 on 2007-03-03
> **phossal said:**
> I really *can't* make anything out of it. I run from Java exceptions. ;) I haven't actually used a packaged version of Java for a long time, and I haven't used anything but the .tar.gz version of the *wires. Launching them has never really been an issue. You're not running something else that might impact them are you, like Beryl?
I just get Java from Sun's web site, build the .deb, and install it - nothing fancy. Up to the last release of Frostwire, I never had any problems. And as far as anything that might be interfering, I gave up on Beryl (for now) due to ATI's <insert appropriate insulting adjective here> inability to make their drivers support compositing to use AIGLX, and I refuse to use XGL as it is horridly slow. So AFAIK, nothing interfering with it. Thanks for the suggestion though.

---

### Post by phossal on 2007-03-03
You build a deb for Java? Interesting. How do you get FrostWire?

---

### Post by amaan on 2007-03-03
hey when i try running frostwire i get a blank grey screen after the frostwire status window comes ? what do i do?

---

### Post by Perfect Storm on 2007-03-03
Let me guess...You have beryl installed?
If so just switch to metcity when using frostwire.

---

### Post by phossal on 2007-03-03
Man, that is a *creepy* looking icon. It looks like something that belongs in a rat trap.

---

### Post by Perfect Storm on 2007-03-03
:mrgreen: :mrgreen: :mrgreen:

---

### Post by rainwalker on 2007-03-07
So FrostWire doesn't work with Beryl running, but if I right-click on the beryl-manager icon and choose "Select Window Manager -> Metacity (Gnome Window Manager)" it should work, right?

---

### Post by Perfect Storm on 2007-03-08
Aye. That is what I'm doing.

---

### Post by j.miller565 on 2007-03-08
oh man this is great. I seriously can't wait to use it.

---

### Post by rainwalker on 2007-03-08
Okay, it works (I think, I got it installed and it starts, but I have yet to try it with Metacity (it gray-screens in Beryl)) but can I move the stuff that's on my desktop to the trash? I like my desktop to be clear. FYI, I've got the java .bin file and the jre1.5.0_11 folder on my desktop, those are what I'm talking about deleting

---

### Post by rainwalker on 2007-03-08
Works PERFECTLY (except for the chat thing and the system tray icon), thanks!

---

### Post by julie_lebou on 2007-03-20
ok, i did everything, and it all went fine... but after i write yes, and im ''done''

what do I do to install/start Frostwire? It just says in the ''How to''

code: frostwire.. and that dosent work

---

### Post by Panzor on 2007-03-26
> **SSupport said:**
> Had some issues getting things working myself. I installed the .deb package, and it installed no problem- icon was in the Application panel....but when I clicked on the icon, it did nothing.

Found that going through Synaptic, and right-clicking on frostwire, it gives the option to "Mark Suggested for Installation"  the missing pieces of Java needed to run.  Once I downloaded the missing 5 files, it ran with no issues.  

Hope this helps other n3wbs like myself.  :D

Thank you so much! This worked for me.

---

### Post by LukeCarrier on 2007-05-19
This howto is useless, its outdated and has failed completely with feisty, UPDATE IT!frostwire

---

### Post by Robor on 2007-05-21
> **LukeCarrier said:**
> This howto is useless, its outdated and has failed completely with feisty, UPDATE IT!frostwire

Yep...  Doesn't work anymore.  Downloads index.html.1 and that's it.  Trying to find another install howto here.

---

### Post by fastpakr on 2007-05-21
Are you having trouble with installing Frostwire via Add/Remove in Feisty?

---

### Post by rahimveron on 2007-11-16
Just install the deb from Frostwire website and the problems with Beryl/Comiz is sorted out in version 4.13.3

---

### Post by reverend_HH on 2007-11-26
so i take it we're stuck with no system tray icon?

---

### Post by rainwalker on 2007-11-26
> **reverend_HH said:**
> so i take it we're stuck with no system tray icon?

Correct.

---

### Post by reverend_HH on 2007-11-26
> **rainwalker said:**
> Correct.

was there ever a system tray icon? im pretty sure i remember there being one before

---

### Post by rainwalker on 2007-11-26
> **reverend_HH said:**
> was there ever a system tray icon? im pretty sure i remember there being one before

Yeah there was, but that was waayyy back
I think I was on Edgy when they had a system tray icon, so that would be at least a year ago

---

### Post by kyren on 2007-12-11
I couldnt get   "jre-6u3-linux-i586.bin"  into the usr/java folder. It can't be manually moved in my account, and I can't figure out how to log in as root. i tried following instructions to the letter, but got erors at entering "chmod a+x jre-6u2-linux-i586.bin"

    someone please tell me how to do this :l

---

### Post by FuturePilot on 2007-12-11
> **kyren said:**
> I couldnt get   "jre-6u3-linux-i586.bin"  into the usr/java folder. It can't be manually moved in my account, and I can't figure out how to log in as root. i tried following instructions to the letter, but got erors at entering "chmod a+x jre-6u2-linux-i586.bin"

    someone please tell me how to do this :l

This guide is old. That part shouldn't be necessary anymore. Just install Java through the repos.
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

