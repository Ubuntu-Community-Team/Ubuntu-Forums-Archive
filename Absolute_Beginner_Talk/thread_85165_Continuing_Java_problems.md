---
title: "Continuing Java problems"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by VladTheImpaler on 2005-11-01
I've searched, read, posted questions and followed all advice to get Java runtime installed and configured.  I thought all was well.

When I check java -version I see this:

java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

I visited a website that supports audio streaming with a java applet.  The audio stream does not work and the java window has a red x in the upper left corner.  Right clicking  the window opens a java console which displays:

Java(TM) Plug-in: Version 1.4.2
Using JRE version 1.4.2-02 Java HotSpot(TM) Client VM
User home directory = /home/jay
Proxy Configuration: Browser Proxy Configuration


----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
p:   reload proxy configuration
q:   hide console
r:   reload policy configuration
s:   dump system properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------
load: class WMPNS.WMP not found.
java.lang.ClassNotFoundException: WMPNS.WMP
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:162)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:123)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:566)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:619)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:1879)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:548)
	at sun.applet.AppletPanel.run(AppletPanel.java:299)
	at java.lang.Thread.run(Thread.java:534)
Caused by: java.io.IOException: open HTTP connection failed.
	at sun.applet.AppletClassLoader.getBytes(AppletClassLoader.java:265)
	at sun.applet.AppletClassLoader.access$100(AppletClassLoader.java:43)
	at sun.applet.AppletClassLoader$1.run(AppletClassLoader.java:152)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:149)
	... 9 more
java.lang.IllegalArgumentException: null source
	at java.util.EventObject.<init>(EventObject.java:34)
	at java.awt.AWTEvent.<init>(AWTEvent.java:225)
	at java.awt.event.ComponentEvent.<init>(ComponentEvent.java:94)
	at java.awt.event.WindowEvent.<init>(WindowEvent.java:174)
	at java.awt.event.WindowEvent.<init>(WindowEvent.java:211)
	at java.awt.DefaultKeyboardFocusManager.dispatchEvent(DefaultKeyboardFocusManager.java:576)
	at java.awt.Component.dispatchEventImpl(Component.java:3506)
	at java.awt.Container.dispatchEventImpl(Container.java:1627)
	at java.awt.Window.dispatchEventImpl(Window.java:1606)
	at java.awt.Component.dispatchEvent(Component.java:3477)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:456)
	at java.awt.SequencedEvent.dispatch(SequencedEvent.java:93)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:454)
	at java.awt.EventDispatchThread.pumpOneEventForHierarchy(EventDispatchThread.java:201)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:151)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:145)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:137)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:100)
java.lang.IllegalArgumentException: null source
	at java.util.EventObject.<init>(EventObject.java:34)
	at java.awt.AWTEvent.<init>(AWTEvent.java:225)
	at java.awt.event.ComponentEvent.<init>(ComponentEvent.java:94)
	at java.awt.event.WindowEvent.<init>(WindowEvent.java:174)
	at java.awt.event.WindowEvent.<init>(WindowEvent.java:211)
	at java.awt.DefaultKeyboardFocusManager.dispatchEvent(DefaultKeyboardFocusManager.java:576)
	at java.awt.Component.dispatchEventImpl(Component.java:3506)
	at java.awt.Container.dispatchEventImpl(Container.java:1627)
	at java.awt.Window.dispatchEventImpl(Window.java:1606)
	at java.awt.Component.dispatchEvent(Component.java:3477)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:456)
	at java.awt.SequencedEvent.dispatch(SequencedEvent.java:93)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:454)
	at java.awt.EventDispatchThread.pumpOneEventForHierarchy(EventDispatchThread.java:201)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:151)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:145)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:137)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:100)
java.lang.IllegalArgumentException: null source
	at java.util.EventObject.<init>(EventObject.java:34)
	at java.awt.AWTEvent.<init>(AWTEvent.java:225)
	at java.awt.event.ComponentEvent.<init>(ComponentEvent.java:94)
	at java.awt.event.WindowEvent.<init>(WindowEvent.java:174)
	at java.awt.event.WindowEvent.<init>(WindowEvent.java:211)
	at java.awt.DefaultKeyboardFocusManager.dispatchEvent(DefaultKeyboardFocusManager.java:576)
	at java.awt.Component.dispatchEventImpl(Component.java:3506)
	at java.awt.Container.dispatchEventImpl(Container.java:1627)
	at java.awt.Window.dispatchEventImpl(Window.java:1606)
	at java.awt.Component.dispatchEvent(Component.java:3477)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:456)
	at java.awt.SequencedEvent.dispatch(SequencedEvent.java:93)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:454)
	at java.awt.EventDispatchThread.pumpOneEventForHierarchy(EventDispatchThread.java:201)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:151)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:145)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:137)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:100)
load: class WMPNS.WMP not found.
java.lang.ClassNotFoundException: WMPNS.WMP
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:162)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:123)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:566)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:619)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:1879)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:548)
	at sun.applet.AppletPanel.run(AppletPanel.java:299)
	at java.lang.Thread.run(Thread.java:534)
Caused by: java.io.IOException: open HTTP connection failed.
	at sun.applet.AppletClassLoader.getBytes(AppletClassLoader.java:265)
	at sun.applet.AppletClassLoader.access$100(AppletClassLoader.java:43)
	at sun.applet.AppletClassLoader$1.run(AppletClassLoader.java:152)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:149)
	... 9 more

I am obviously not configured correctly yet.  What should I try now?  Thanks again for your help and patience.

Vlad

---

### Post by gord on 2005-11-02
and chance of what browser you are using? java doesn't work for me in the new firefox beta's but works fine in the regular version

---

### Post by paddyg on 2005-11-02
[QUOTE=VladTheImpaler]
When I check java -version I see this:

java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

[/QUOTE]

vlad,
i'm curious, what does firefox say about java when you type
```
about:plugins
```
in its navigation bar?

---

