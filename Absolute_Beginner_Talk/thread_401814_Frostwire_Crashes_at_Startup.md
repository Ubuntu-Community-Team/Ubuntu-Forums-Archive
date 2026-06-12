---
title: "Frostwire Crashes at Startup"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by EerFoolWVU on 2007-04-05
Whenever I startup Frostwire, as soon as it finishes loading up it crashes and disappears.....anybody know why its doing this and how I can go about fixing this?

---

### Post by EerFoolWVU on 2007-04-05
bump

---

### Post by taurus on 2007-04-05
Open a terminal and run it so you at least can see what is wrong with it.

Applications -> Accessories -> Terminal
```
frostwire
```
p.s.  Do you have java installed on your machine?

```
java -version
```

---

### Post by Sweet Spot on 2007-04-05
I just installed FW and am experiencing the same thing. This is the output in the terminal (the end part anyway): > Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@24de7d
current thread is Thread[main,5,main]
please submit a bug report to [EMAIL="bugs@frostwire.com"]bugs@frostwire.com[/EMAIL] with the following information :
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
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl. java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces sorImpl.java:25)
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(Cha tMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java :104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.ja va:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:25 6)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl. java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces sorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
#
[B]# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb10e4b02, pid=23601, tid=2968087472
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x34b02]
#
# An error report file with more information is saved as hs_err_pid23601.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 122: 23601 Aborted                 ${JA VA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logg ing.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)[/B]


So then the answer is to roll back to JRE v. 1.4 ? How should I do that, and is it even worth it to do in the first place ?

---

### Post by Punker on 2007-04-05
hey speaking about frostwire I been looking for ports to allow for frostwire to connect
frostwire just says opening connection but it never connects I was wondering if you guys knew or had this problem I looked in the forum and around google but everything out their I had no luck with

---

### Post by dkeats on 2007-04-07
> **Sweet Spot said:**
> I just installed FW and am experiencing the same thing. This is the output in the terminal (the end part anyway): 

So then the answer is to roll back to JRE v. 1.4 ? How should I do that, and is it even worth it to do in the first place ?

I found that I had updated to SUN Java 6, but still had Java 5 installed. I removed Java 5 and ran 

 sudo update-alternatives --config java

After that Frostwire seems to be OK.

---

### Post by Entity` on 2008-03-15
The same thing is happening to me... in windows XP!!!.  Its aggravating me really bad cuz I can't use it at all.  Even the latest version crashes even before its done loading.  This just isn't cool.

---

