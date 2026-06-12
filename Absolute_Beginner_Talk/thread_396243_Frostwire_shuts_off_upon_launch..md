---
title: "Frostwire shuts off upon launch."
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-03-29
What the title says. I've done nothing except gotten the latest updates the other day and this is what happened to it. 

When I launch frostwire from terminal:


jason@jason:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading FrostWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-misc-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:141)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:102)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:70)
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
expected thread was [Lirc.DispatchThread;@48f675
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:141)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:102)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:70)
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
expected thread was [Lirc.DispatchThread;@48f675
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:141)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:102)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:70)
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
expected thread was [Lirc.DispatchThread;@48f675
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:141)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:102)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:70)
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
expected thread was [Lirc.DispatchThread;@48f675
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:141)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:102)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:70)
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
expected thread was [Lirc.DispatchThread;@48f675
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:141)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:102)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:70)
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
#  SIGSEGV (0xb) at pc=0xb0db3b70, pid=30604, tid=2963639200
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2eb70]
#
# An error report file with more information is saved as hs_err_pid30604.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 122: 30604 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

jason@jason:~$

---

### Post by Roasted on 2007-03-30
Also, it seems to go randomly. Just now I got it to stay up for about 20 seconds. I searched for some Incubus stuff and the search returned results. I click on one, BAM, shuts off. Whaaaaat?

---

### Post by mahiyar on 2007-03-30
This sure seems to be a java problem, I did this for install [http://ubuntuforums.org/showthread.php?t=305337&highlight=frostwire+install](http://ubuntuforums.org/showthread.php?t=305337&highlight=frostwire+install) this method uses its own java directory to avoid conflicts?

---

### Post by Roasted on 2007-03-30
100%[====================================>] 6,631,282    868.32K/s    ETA 00:00

11:24:49 (811.85 KB/s) - `frostwire-4.13.1.i586.deb' saved [6631282/6631282]

jason@jason:~$ sudo dpkg -i frostwire-4.13.1.i586.deb
Selecting previously deselected package frostwire.
(Reading database ... 160789 files and directories currently installed.)
Unpacking frostwire (from frostwire-4.13.1.i586.deb) ...
Setting up frostwire (4.13.1) ...
jason@jason:~$ sudo mkdir /usr/java
jason@jason:~$ sudo cp jre-1_5_0_11-linux-i586.bin /usr/java
cp: cannot stat `jre-1_5_0_11-linux-i586.bin': No such file or directory
jason@jason:~$ sudo mkdir /usr/java
mkdir: cannot create directory `/usr/java': File exists
jason@jason:~$ sudo cp jre-1_5_0_11-linux-i586.bin /usr/java
cp: cannot stat `jre-1_5_0_11-linux-i586.bin': No such file or directory
jason@jason:~$ 





Why's it do this? mkdir is the command to use, or am I losing it?

---

### Post by mahiyar on 2007-03-30
Are you following the method as given in the link in my post?

---

### Post by Roasted on 2007-03-31
Yeah. That's where I got that error.

---

### Post by mahiyar on 2007-04-01
The jre file that you downloaded might not be in your home directory, it might be on your desktop or something, in that case copy from there.

---

### Post by lolwhites on 2007-04-02
I tried following your instructions but when I got as far as step 2 I got the following error message:


> [http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb](http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb)
           => `frostwire-4.13.1.i586.deb'
Resolving peercommons.com... 208.97.134.26
Connecting to peercommons.com|208.97.134.26|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb](http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb) [following]
--11:15:12--  [http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb](http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb)
           => `frostwire-4.13.1.i586.deb'
Resolving [www.peercommons.com](www.peercommons.com)... 208.97.134.26
Connecting to www.peercommons.com|208.97.134.26|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:15:13 ERROR 404: Not Found.

---

### Post by mahiyar on 2007-04-02
Something wrong with the link, just download the deb file from the original frostwire site from here [http://www.frostwire.com/?id=downloads](http://www.frostwire.com/?id=downloads) . Install the deb file and put the java folder as instructed above and you should be through.

---

### Post by lolwhites on 2007-04-02
Cheers, it seems to work now (touch wood)...

---

### Post by lolwhites on 2007-04-02
Correction - it worked the first time, but after that it started shutting down on launch again. Here's what it said:

> Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading FrostWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-misc-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:141)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:102)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:70)
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
expected thread was [Lirc.DispatchThread;@1a3ca10
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:141)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:102)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:70)
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
expected thread was [Lirc.DispatchThread;@1a3ca10
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:141)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:102)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:70)
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
expected thread was [Lirc.DispatchThread;@1a3ca10
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:141)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:102)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:70)
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
expected thread was [Lirc.DispatchThread;@1a3ca10
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:141)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:102)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:70)
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
expected thread was [Lirc.DispatchThread;@1a3ca10
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:141)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:102)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:70)
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
#  SIGSEGV (0xb) at pc=0xb0e1f598, pid=13401, tid=2964089760
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2c598]
#
# An error report file with more information is saved as hs_err_pid13401.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 122: 13401 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

---

### Post by Roasted on 2007-04-06
> **mahiyar said:**
> The jre file that you downloaded might not be in your home directory, it might be on your desktop or something, in that case copy from there.

There's nothing on my desktop. How can I locate this JRE file?

---

### Post by mahiyar on 2007-04-06
From nautilus use the search function or better still use terminal and use >locate jre* command.

---

### Post by Roasted on 2007-04-07
I've got some options here.



/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Cambridge_Bay
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Dominica
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Puerto_Rico
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Denver
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Barbados
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Grenada
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Chihuahua
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Yellowknife
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Cayman
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/St_Johns
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Detroit
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Atikokan
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Nassau
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Swift_Current
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Hermosillo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Whitehorse
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Boise
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/St_Kitts
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Havana
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Pangnirtung
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Blanc-Sablon
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Thunder_Bay
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Guadeloupe
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Toronto
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Rainy_River
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Chicago
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Montserrat
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Merida
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Menominee
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Miquelon
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Mazatlan
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Iqaluit
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Juneau
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Costa_Rica
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Monterrey
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/La_Paz
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Fortaleza
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Cayenne
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Argentina
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Argentina/Rio_Gallegos
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Argentina/Catamarca
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Argentina/San_Juan
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Argentina/Tucuman
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Argentina/La_Rioja
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Argentina/Mendoza
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Argentina/Jujuy
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Argentina/Buenos_Aires
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Argentina/Cordoba
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Argentina/Ushuaia
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Aruba
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Port_of_Spain
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Bogota
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Paramaribo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Manaus
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Campo_Grande
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Bahia
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Curacao
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Maceio
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Rio_Branco
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Asuncion
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Santiago
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Caracas
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Montevideo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Guayaquil
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Cuiaba
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Guyana
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Belem
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Sao_Paulo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Eirunepe
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Recife
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Boa_Vista
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Porto_Velho
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Araguaina
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Lima
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/America/Noronha
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Atlantic
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Atlantic/South_Georgia
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Atlantic/St_Helena
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Atlantic/Cape_Verde
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Atlantic/Reykjavik
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Atlantic/Faeroe
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Atlantic/Canary
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Atlantic/Azores
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Atlantic/Madeira
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Atlantic/Bermuda
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Atlantic/Stanley
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Hong_Kong
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Oral
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Taipei
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Damascus
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Tokyo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Muscat
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Bangkok
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Yerevan
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Kashgar
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Shanghai
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Kuching
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Colombo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Pontianak
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Karachi
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Bishkek
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Hovd
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Dili
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Kabul
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Qatar
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Katmandu
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Aqtobe
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Nicosia
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Kuala_Lumpur
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Makassar
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Tashkent
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Manila
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Phnom_Penh
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Jakarta
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Bahrain
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Ashgabat
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Macau
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Jerusalem
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Amman
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Baku
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Seoul
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Rangoon
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Dubai
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Harbin
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Calcutta
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Qyzylorda
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Chongqing
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Samarkand
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Thimphu
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Saigon
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Urumqi
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Riyadh
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Aden
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Gaza
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Jayapura
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Beirut
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Choibalsan
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Kuwait
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Ulaanbaatar
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Vientiane
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Tehran
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Pyongyang
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Brunei
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Almaty
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Aqtau
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Tbilisi
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Baghdad
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Dhaka
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Yekaterinburg
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Singapore
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Dushanbe
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Yakutsk
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Magadan
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Vladivostok
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Anadyr
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Omsk
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Novosibirsk
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Sakhalin
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Krasnoyarsk
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Irkutsk
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Kamchatka
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Riyadh87
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Riyadh88
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Asia/Riyadh89
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/ZoneInfoMappings
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Australia
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Australia/Brisbane
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Australia/Broken_Hill
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Australia/Darwin
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Australia/Adelaide
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Australia/Lindeman
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Australia/Hobart
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Australia/Melbourne
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Australia/Perth
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Australia/Lord_Howe
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Australia/Sydney
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Australia/Currie
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/CET
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/CST6CDT
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/EET
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/EST
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/EST5EDT
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT-14
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/UTC
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT-13
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT-12
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT-11
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT-10
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT-1
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT+11
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT+12
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT-5
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT+7
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT+10
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT-4
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT+6
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT-3
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT+5
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT-2
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT+4
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT-9
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT+3
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT-8
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT+2
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT-7
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT+1
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT-6
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT+8
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT+9
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/UCT
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Etc/GMT
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Gibraltar
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Samara
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Sofia
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Monaco
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Kaliningrad
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Vienna
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Volgograd
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Malta
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Madrid
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Luxembourg
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Minsk
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Vilnius
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Lisbon
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Riga
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Zurich
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Brussels
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Dublin
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Zaporozhye
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Simferopol
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Oslo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Rome
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Tirane
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Istanbul
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Copenhagen
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Bucharest
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Helsinki
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Tallinn
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Amsterdam
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Athens
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Uzhgorod
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Stockholm
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Berlin
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Andorra
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Chisinau
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Budapest
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Paris
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Vaduz
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Prague
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Kiev
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Warsaw
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Belgrade
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/London
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Europe/Moscow
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/GMT
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/HST
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Indian
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Indian/Antananarivo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Indian/Mahe
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Indian/Comoro
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Indian/Mauritius
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Indian/Mayotte
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Indian/Kerguelen
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Indian/Reunion
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Indian/Maldives
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Indian/Chagos
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Indian/Christmas
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Indian/Cocos
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/MET
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/MST
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/MST7MDT
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/PST8PDT
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Funafuti
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Tahiti
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Port_Moresby
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Kiritimati
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Rarotonga
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Tarawa
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Majuro
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Fiji
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Pitcairn
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Ponape
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Kosrae
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Auckland
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Wallis
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Efate
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Johnston
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Guadalcanal
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Norfolk
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Midway
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Niue
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Guam
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Pago_Pago
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Palau
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Tongatapu
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Nauru
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Gambier
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Apia
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Chatham
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Kwajalein
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Marquesas
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Saipan
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Enderbury
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Wake
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Fakaofo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Noumea
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Honolulu
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Truk
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Galapagos
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/Pacific/Easter
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/SystemV
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/SystemV/PST8PDT
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/SystemV/YST9
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/SystemV/CST6CDT
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/SystemV/CST6
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/SystemV/MST7
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/SystemV/YST9YDT
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/SystemV/HST10
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/SystemV/EST5
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/SystemV/PST8
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/SystemV/AST4ADT
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/SystemV/AST4
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/SystemV/MST7MDT
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/SystemV/EST5EDT
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/zi/WET
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/charsets.jar
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/jce.jar
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/COPYRIGHT
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/README
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7-gcc29
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/desktop
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/desktop/sun_java.desktop
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/desktop/sun_java.png
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/javaws
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/javaws/javaws
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/LICENSE
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/THIRDPARTYLICENSEREADME.txt
/usr/lib/sablevm/jre
/usr/lib/sablevm/jre/lib
/usr/lib/sablevm/jre/lib/libclasspath.jar
/usr/lib/sablevm/jre/lib/resources.jar
/usr/lib/sablevm/jre/lib/rt.jar
/usr/lib/sablevm/jre/bin
/usr/lib/fjsdk/jre
/usr/lib/fjsdk/jre/lib
/usr/lib/fjsdk/jre/lib/rt.jar
/usr/lib/fjsdk/jre/lib/ext
/usr/lib/fjsdk/jre/bin
/usr/share/app-install/icons/_usr_lib_j2se_1.4_jre_plugin_desktop_sun_java.png
/usr/share/doc/sun-java5-jre
/usr/share/doc/sun-java5-jre/README.alternatives
/usr/share/doc/sun-java5-jre/JAVA_HOME
/usr/share/doc/sun-java5-jre/README.Debian
/usr/share/doc/sun-java5-jre/TODO.Debian
/usr/share/doc/sun-java5-jre/copyright
/usr/share/doc/sun-java5-jre/changelog.gz
/usr/share/doc/sun-java5-jre/README.gz
/usr/share/doc/sun-java5-jre/changelog.Debian.gz
/usr/share/doc/sun-java5-jre/CHANGES.gz
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/linux
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/linux/jreinstallers
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/linux/jreinstallers/j2re1_4_2
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/linux/jreinstallers/j2re1_4_2/GNUmakefile
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/linux/jreinstallers/resources
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/linux/jreinstallers/resources/javaws-1_0_1-j2re-1_4_2-linux-i586.jnlp
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/linux/jreinstallers/resources/version.xml_linux-i586_1.4.2
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/linux/jreinstallers/GNUmakefile
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/linux/minclude
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/linux/minclude/linux.defs
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/share
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/share/jreinstallers
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/share/jreinstallers/bundle.unix.gmk
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/share/jreinstallers/components.gmk
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/share/jreinstallers/installer.gmk
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/share/Platform.gmk
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/solaris
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/solaris/jreinstallers
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/solaris/jreinstallers/j2re1_4_2
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/solaris/jreinstallers/j2re1_4_2/GNUmakefile
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/solaris/jreinstallers/resources
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/solaris/jreinstallers/resources/javaws-1_0_1-j2re-1_4_2-solaris-sparc.jnlp
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/solaris/jreinstallers/resources/version.xml_solaris-sparc_1.4.2
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/solaris/jreinstallers/GNUmakefile
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/solaris/minclude
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/solaris/minclude/solaris.defs
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/win32
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/win32/jreinstallers
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/win32/jreinstallers/bundle.win.gmk
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/win32/jreinstallers/j2re1_4_2
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/win32/jreinstallers/j2re1_4_2/GNUmakefile
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/win32/jreinstallers/GNUmakefile
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/win32/jreinstallers/resources
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/win32/jreinstallers/resources/javaws-1_0_1-j2re-1_4_2-windows-i586.jnlp
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/win32/jreinstallers/resources/version.xml_windows-i586_1.4.2
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/win32/minclude
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/build/win32/minclude/windows.defs
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/WinRegistry.java
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/resources
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/resources/strings_zh_CN.properties
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/resources/strings_sv.properties
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/resources/strings.properties
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/resources/strings_de.properties
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/resources/strings_es.properties
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/resources/strings_fr.properties
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/resources/strings_it.properties
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/resources/strings_ja.properties
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/resources/sunLogo.gif
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/resources/strings_ko.properties
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/resources/strings_zh_TW.properties
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/Config.java
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/Main.java
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/SolarisInstaller.java
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/share/classes/jnlp/sample/JreInstaller/WindowsInstaller.java
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/win32
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/win32/jreinstallers
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/win32/jreinstallers/WindowsInstaller.c
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/win32/jreinstallers/registry.cpp.gz
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/src/win32/jreinstallers/versionChecker.c.gz
/usr/share/doc/sun-java5-jdk/examples/jnlp/jreinstaller/README
/usr/share/doc/sun-java6-jre
/usr/share/doc/sun-java6-jre/README.alternatives
/usr/share/doc/sun-java6-jre/JAVA_HOME
/usr/share/doc/sun-java6-jre/README.Debian
/usr/share/doc/sun-java6-jre/TODO.Debian
/usr/share/doc/sun-java6-jre/copyright
/usr/share/doc/sun-java6-jre/README.gz
/usr/share/doc/sun-java6-jre/changelog.Debian.gz
/usr/share/lintian/overrides/sun-java5-jre
/usr/share/lintian/overrides/sun-java6-jre
/usr/share/mime/packages/sun-java5-jre.xml
/usr/share/mime/packages/sun-java6-jre.xml
jason@jason:~$

---

### Post by Roasted on 2007-04-07
I tried installing automatix 1. Somehow, frostwire works now. I failed at installing automatix 1 for some reason. *shrug* Just gave me errors so I gave up.

---

### Post by Roasted on 2007-04-08
All right. This is getting old. What else can I do to fix this? I can't seem to get automatix 1 installed, which from what I remember has the java. I can't find the java in automatix 2. What can I do?

---

### Post by mahiyar on 2007-04-08
All right folks .... It seems that the newer version of frostwire with chat windows is the one causing problems. I ran into a similar trouble when I updated my version of frostwire from peercommons/beta to the edgy one. When I removed the edgy version and went back to the beta version without chat windows, frostwire worked fine. Now the problem is that the deb file at peercommons is no longer available. I have that deb file, if any body wants it please suggest how where do I upload.

---

### Post by SwordRaven on 2007-04-08
[http://www.wikiupload.com/](http://www.wikiupload.com/)

that looks like an interesting project, you could try there?

Cheers

---

### Post by mahiyar on 2007-04-08
Thanks SwordRaven, thats a pretty nifty tool to have. OK the download link is [http://www.wikiupload.com/download_page.php?id=121683](http://www.wikiupload.com/download_page.php?id=121683) , push the download button, enter the displayed characters in the box and "get" it.

---

### Post by SwordRaven on 2007-04-08
> **mahiyar said:**
> Thanks SwordRaven, thats a pretty nifty tool to have. OK the download link is [http://www.wikiupload.com/download_page.php?id=121683](http://www.wikiupload.com/download_page.php?id=121683) , push the download button, enter the displayed characters in the box and "get" it.

Champion, cheers!

Their site needs a LOT of work but it does look like a project to keep an eye on imo.

---

### Post by mahiyar on 2007-04-08
Ok to sum up the procedure to install frostwire. This is originally by motorhead, follow this link [http://ubuntuforums.org/showthread.php?t=305337&highlight=frostwire+install](http://ubuntuforums.org/showthread.php?t=305337&highlight=frostwire+install) However in step 2 instead of downloading from the peercommon link, follow this ...

2. we download it and install it
Click on the link below to download
[http://www.wikiupload.com/download_page.php?id=121683](http://www.wikiupload.com/download_page.php?id=121683)

Double click the deb file to open the deb installer.

Next steps are as in the ubuntuforums link by motorhead

---

### Post by mahiyar on 2007-04-08
Roasted -- It is pretty clear that the file required is not to be seen anywhere in your long ct&pst job. Download it again and take care to see where it gets downloaded.

---

### Post by mahiyar on 2007-04-10
Peercommons site is ON again, so you can use the original thread.

---

### Post by Roasted on 2007-05-05
Somehow it was fixed, yet somehow it's doing it again.

How can I just get an older version? This is getting old... Very old...

---

### Post by dbqp on 2007-05-13
I was having the same problem, but I followed the command from this link and all was working within 30 seconds...I had previously uninstalled FrostWire and then after I made the change, I reinstalled FW.

command:
after you have java 6 installed go back to terminal and type...
Quote:
sudo update-alternatives --config java
...this will list all java virtual machines installed and allow you to choose the default ...java 6 of course


[http://ubuntuforums.org/showthread.php?t=407537&highlight=frostwire]("http://ubuntuforums.org/showthread.php?t=407537&highlight=frostwire")

Hope it helps some of you out!

---

### Post by Roasted on 2007-05-14
I think that worked. Thanks! No problems here yet.

What does that do though? Do I essentially have more than 1 java installed and I just needed to specify which takes control first?

---

### Post by dbqp on 2007-05-14
> **Roasted said:**
> I think that worked. Thanks! No problems here yet.

What does that do though? Do I essentially have more than 1 java installed and I just needed to specify which takes control first?

Great to hear the feedback! I only hope it helps SOMEBODY when I add my searches and own encounters.

What you are doing is just telling the system that you want version 1.0.6 JRE to be used as the default. When you ran this command, you should have seen an astrick in the left column from 1.0.5. You just set your system default to the higher version.

Now, I don't know what kind of impact this would have on various other applications installed as everyone has a different config and apps installed.

Post back if you run into issues in other apps/settings or even if everything stays stable after awhile!

dbqp

---

### Post by Roasted on 2007-05-14
The only thing is, this solution I haven't seen before, so I wonder how other users have dealt with this issue I had? Did they just completely uninstall ALL of the other versions of java, leaving only the one they needed? Whereas I simply set the default to the one I needed and that was it?

---

