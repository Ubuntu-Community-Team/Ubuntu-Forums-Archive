---
title: "So I Just Installed Frostwire..."
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Biscuitpie on 2007-04-07
And it won't load from the Applications menu. I opened up terminal and typed frostwire, here's what I got:

```

andrew@andrew-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
ls: /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com

```

I have no clue what to do.

---

### Post by tdwester on 2007-04-07
You need to install java.

---

### Post by Bachstelze on 2007-04-07
[https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

Instructions to install the JRE are there ;)

---

### Post by Biscuitpie on 2007-04-07
Thanks a lot, Hymn.

---

### Post by gustasonfrever on 2007-04-07
I have followed all of these instructions but now I'm prompted with an error message when I follow Applications>Internet>Frostwire "Could Not Launch Menu Item
 Failed to execute child process "U" (no such file or directory) 
Do you know what I can do to solve this problem?

---

### Post by Bachstelze on 2007-04-07
Try to run frostwire from a terminal and paste the error messages you get, if any.

---

### Post by gustasonfrever on 2007-04-07
gustason@gustason-laptop:~$ frostwire
bash: frostwire: command not found

---

### Post by Biscuitpie on 2007-04-07
Where did you install Frostwire from? I got mine from their website and it automatically installed. If you didn't do that, I'd try it.

---

### Post by gustasonfrever on 2007-04-07
well I just tried this but when I double click on the .deb file on the desktop I eventually come to the message that  Ican only have one software management program opened at once. But I don't have any other programs on so I have no idea what is going wrong with ubuntu.

---

### Post by Maestro23 on 2007-04-07
Wanted to see for myself.  Just download[COLOR="Red"] frostwire-4.13.1.6.i586.deb[/COLOR] from their site.  Then installed the .deb

> sudo dpkg -i frostwire-4.13.1.6.i586.deb

Installed with no errors.  Even put the blank window icon in my menu(will fix that later) Apps>>Internet.

Then click on that icon and the setup window for frostwire came up.  Setup/configured it and it is up and running as I type this.

*Running Feisty 7.04 w/java6 from the repositories.

---

### Post by gustasonfrever on 2007-04-07
gustason@gustason-laptop:~$ sudo dpkg -i frostwire-4.13.1.6.i586.deb
Password:
dpkg: error processing frostwire-4.13.1.6.i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 frostwire-4.13.1.6.i586.deb
I'm starting to change my mind about ubuntu, so far nothing I have installed has worked and its very frustrating.

---

### Post by Bachstelze on 2007-04-07
Obviously, if you're telling dpkg to install a package that is not there, it won't work...

---

### Post by gustasonfrever on 2007-04-07
How can I get java6? I'm using something that shows up in System>Preferences as Java 1.4.

---

### Post by gustasonfrever on 2007-04-07
Well I have the package on my desktop its fairly evident -at least to me- that it is indeed there.

---

### Post by Maestro23 on 2007-04-07
> **gustasonfrever said:**
> How can I get java6? I'm using something that shows up in System>Preferences as Java 1.4.

First see if it's in your Repositories.  Search in Synaptic for "java6" or command line

> apt-cache search java6

*Like the person above posted, are you in the directory  that the .deb file is in when you run the "sudo dpkg -i" command?

*Edit.  It's on your desktop.  In terminal:

> cd /home/username/Desktop

ls (lists contents of present directory)

also pwd (tells you your current location)


---

### Post by gustasonfrever on 2007-04-07
I have no idea what you are talking about. How does this at all relate to me installing frostwire? 
I can see frostwire when I go from applications>internet and the icon is visible. However, when I click on the icon I get a "could not launch menu item Failed to execute process "u" (no such file or directory)

---

### Post by Maestro23 on 2007-04-07
> **gustasonfrever said:**
> I have no idea what you are talking about. How does this at all relate to me installing frostwire? 
I can see frostwire when I go from applications>internet and the icon is visible. However, when I click on the icon I get a "could not launch menu item Failed to execute process "u" (no such file or directory)

If you frostwire is installed, the following commands will tell you.  In terminal please do the following:

> 1. sudo updatedb (will take about a minute or so)

2. locate frostwire (should see all references to frostwire on your system)

3. whereis frostwire (should give the path to the bin file)


If your installed frostwire correctly, you should get feedback from steps 2 & 3.  You should also be able to start frostwire from command line by typing: frostwire

I believe the menu entry is broken or pointing to a file that is not there.  Much like in Windows sometimes when you uninstall a program and the shortcut is still there are the entry in "Start Programs" remains.  After this, we can see where we need to go next.

---

### Post by gustasonfrever on 2007-04-07
Thanks I appreciate the help. However the first command line you gave me does not do anything in terminal, in fact it simply brings up a new, fresh command line. Do I need to do something with frostwire before I input this command?
I tried your second line however and this is what showed up:
gustason@gustason-laptop:~$ locate frostwire
/var/cache/apt/archives/frostwire_4.13.1-6~edgy3_i386.deb
/var/lib/dpkg/info/frostwire.list
/home/gustason/.local/share/applications/frostwire.desktop
/usr/lib/frostwire
/usr/lib/frostwire/commons-logging.jar
/usr/lib/frostwire/clink.jar
/usr/lib/frostwire/jcraft.jar
/usr/lib/frostwire/irc.jar
/usr/lib/frostwire/commons-httpclient.jar
/usr/lib/frostwire/commons-net.jar
/usr/lib/frostwire/commons-pool.jar
/usr/lib/frostwire/daap.jar
/usr/lib/frostwire/FrostWire.jar
/usr/lib/frostwire/i18n.jar
/usr/lib/frostwire/icu4j.jar
/usr/lib/frostwire/id3v2.jar
/usr/lib/frostwire/jdic_stub.jar
/usr/lib/frostwire/jdic.jar
/usr/lib/frostwire/MessagesBundles.jar
/usr/lib/frostwire/jl011.jar
/usr/lib/frostwire/jmdns.jar
/usr/lib/frostwire/log4j.jar
/usr/lib/frostwire/looks.jar
/usr/lib/frostwire/ProgressTabs.jar
/usr/lib/frostwire/mp3sp14.jar
/usr/lib/frostwire/tritonus.jar
/usr/lib/frostwire/themes.jar
/usr/lib/frostwire/xml-apis.jar
/usr/lib/frostwire/vorbis.jar
/usr/lib/frostwire/log4j.properties
/usr/lib/frostwire/libjdic.so
/usr/lib/frostwire/libtray.so
/usr/lib/frostwire/runFrostwire.sh
/usr/lib/frostwire/libmozembed-linux-gtk1.2.so
/usr/lib/frostwire/libmozembed-linux-gtk2.so
/usr/lib/frostwire/xml.war
/usr/lib/frostwire/FrostWire.icns
/usr/lib/frostwire/MessagesBundle.properties
/usr/lib/frostwire/update.ver
/usr/lib/frostwire/pmf.ico
/usr/lib/frostwire/root
/usr/lib/frostwire/root/magnet10
/usr/lib/frostwire/root/magnet10/limewire.gif
/usr/lib/frostwire/root/magnet10/silentdetect.js
/usr/lib/frostwire/root/magnet10/options.js
/usr/lib/frostwire/root/magnet10/canHandle.img
/usr/lib/frostwire/root/magnet10/badge.img
/usr/lib/frostwire/hashes
/usr/share/applications/frostwire.desktop
/usr/share/doc/frostwire
/usr/share/doc/frostwire/changelog
/usr/share/icons/hicolor/16x16/apps/frostwire.png
/usr/share/icons/hicolor/16x16/apps/.svn/prop-base/frostwire.png.svn-base
/usr/share/icons/hicolor/16x16/apps/.svn/text-base/frostwire.png.svn-base
/usr/share/icons/hicolor/32x32/apps/frostwire.png
/usr/share/icons/hicolor/32x32/apps/.svn/prop-base/frostwire.png.svn-base
/usr/share/icons/hicolor/32x32/apps/.svn/text-base/frostwire.png.svn-base
/usr/share/icons/hicolor/48x48/apps/frostwire.png
/usr/share/icons/hicolor/48x48/apps/.svn/prop-base/frostwire.png.svn-base
/usr/share/icons/hicolor/48x48/apps/.svn/text-base/frostwire.png.svn-base
/usr/share/icons/hicolor/64x64/apps/frostwire.png
/usr/share/icons/hicolor/64x64/apps/.svn/prop-base/frostwire.png.svn-base
/usr/share/icons/hicolor/64x64/apps/.svn/text-base/frostwire.png.svn-base

then using your 3rd step i get this 
frostwire: /usr/lib/frostwire

---

### Post by Maestro23 on 2007-04-08
Ok.  That first command doesn't give any feedback.  It just indexes your database again for searching.  

Looks like frostwire installed.  And you still can't run it from terminal with: frostwire

When I run the [COLOR="Red"]whereis frostwire [/COLOR]command on my system, this is what I get:

>  /usr/bin/frostwire
 /usr/lib/frostwire
 /usr/X11R6/bin/frostwire
 /usr/bin/X11/frostwire



Man, got me stumped here.  Need to grab another Killian's.:)   I'm going to head over to the Frostwire forums, as soon as I get me another adult beverage.:guitar: 

[http://www.frostwire.com/forum/viewforum.php?f=1&sid=993ecc6880d9b1fa6e81dd451c22a77b](http://www.frostwire.com/forum/viewforum.php?f=1&sid=993ecc6880d9b1fa6e81dd451c22a77b)

---

### Post by xioumik on 2007-04-09
This is somewhere along the lines...
I installed frostwire(the .deb version):[http://frostwire.com/downloadfile.php?fileid=deb]("http://frostwire.com/downloadfile.php?fileid=deb")
then i ran the installtion process very easy. And then when i go to the menu and open after it loads it just shuts down.

any1 with the same issues?:popcorn:

---

### Post by xioumik on 2007-04-09
Sorry about the double post

I was reading over this topic and i noticed what some1 said so i typed in frostwire in terminal this is what i get:
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_06]
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
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@15d4de6
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
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@15d4de6
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
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@15d4de6
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
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@15d4de6
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
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@15d4de6
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
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb10ebd6f, pid=21749, tid=2968132528
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x30d6f]
#
# An error report file with more information is saved as hs_err_pid21749.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 122: 21749 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS

******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)




Help!!!

---

