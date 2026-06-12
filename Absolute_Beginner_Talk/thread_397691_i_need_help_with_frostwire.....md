---
title: "i need help with frostwire...."
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Catfish_lolipop on 2007-03-31
When I run FrostWire the program itself  will pop up, but if i try to click something nothing happens. all it does is make my computer "beep" everytime i click. another thing is that my desktop is completly black and if i want everything to be normal than i have to move my mouse over my desktop. the only thing i know is that at the top of the window it says "internal error"  by FrostWire. i dont know if anybody understands what i am saying or if i am just putting too much information out there at one time but i would really like to get it going........

---

### Post by InuyashaDuelist on 2007-03-31
Try uninstalling it (sudo aptitude remove frostwire) and reinstalling it. Make sure you have Java installed first.

If this doesn't help, try removing both frostwire as well as java and reinstalling them. (Java first.)

---

### Post by Catfish_lolipop on 2007-03-31
ok ill try that. and when i installed itthe first time, it gave me sun java. im guessing that is the only thing i need for it........

---

### Post by Catfish_lolipop on 2007-03-31
ok..... i reinstalled it again. but this time i downloaded it for windows and opened it with WINE. i dont know what my problem was the first time but it works now.....still kinda crappy but at least it works and it is ALOT better.. thnx

---

### Post by InuyashaDuelist on 2007-03-31
How well did it work when you reinstalled the Linux version?

---

### Post by Catfish_lolipop on 2007-03-31
the same as it did the first time....im gonna just keep playing around with it.

---

### Post by InuyashaDuelist on 2007-03-31
Good to see you got it working, even if it wasn't exactly the most efficient method. :)

---

### Post by MichaelSM on 2007-04-03
So do I. I've got edgy. Two boxes. One works a treat. This one, a mess. Here's my terminal output. Hope someone can assist. Regards, Michael.


margie@margie-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading FrostWire:
java.lang.ClassNotFoundException: irc.plugin.
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at irc.IRCApplication.loadPlugin(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@19b46dc
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1158)
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@19b46dc
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1158)
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@19b46dc
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1158)
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@19b46dc
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1158)
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
        at java.lang.reflect.Method.invoke(Method.java:585)
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@19b46dc
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1158)
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
        at java.lang.reflect.Method.invoke(Method.java:585)
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1043b70, pid=8422, tid=2965892000
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2eb70]
#
# An error report file with more information is saved as hs_err_pid8422.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 122:  8422 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

margie@margie-desktop:~$

---

