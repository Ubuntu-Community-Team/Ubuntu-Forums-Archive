---
title: "installing java 6.1"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by baskettplayr on 2007-05-28
can please help me install the new java 6.1

---

### Post by taurus on 2007-05-28
If you are running Feisty Fawn, you can install Sun version 1.6 from the repos.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-fonts
java -version
```

---

### Post by baskettplayr on 2007-05-28
i will try that and tell u if it works....

---

### Post by baskettplayr on 2007-05-28
hey this is what i got...
[IMG]http://i120.photobucket.com/albums/o164/baskettplayr/Screenshot-kodeykodey.png[/IMG]

---

### Post by baskettplayr on 2007-05-28
bump

---

### Post by taurus on 2007-05-28
Try

```
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-fonts
java -version
```

---

### Post by DougieFresh4U on 2007-05-28
Why can't He try: ** sudo update-alternatives --config java**
And select the java He wants

---

### Post by baskettplayr on 2007-05-28
is this right?
[IMG]http://i120.photobucket.com/albums/o164/baskettplayr/Screenshotfd.png[/IMG]

---

### Post by taurus on 2007-05-28
You have java version 1.6 of your machine now.

---

### Post by discmaster on 2007-05-28
taurus - if I may jump in here... we are trying to get the 6.1 vers. so frostwire will run...it is still not working. :( at least not for me.

---

### Post by baskettplayr on 2007-05-28
thank you!!!!

---

### Post by FerhatBingol on 2007-05-28
-- Removed By Author ---

---

### Post by discmaster on 2007-05-28
How does one gain write permissions to /usr?

---

### Post by taurus on 2007-05-28
Use 

```
gksudo nautilus
```

---

### Post by discmaster on 2007-05-28
Thank you, taurus! 

I did manage to get that far now; I was just typing "sudo" prev., as I thought that would do it.

File & folder is copied over to the usr directory, but I am again stuck from there. Tried to do the "chmod" thing, but it isn't working for me. 

I hope baskettplayr is having better success than I...

---

### Post by taurus on 2007-05-28
It is _not_ a good idea to chmod or chown /usr.  If you do, you will break things.  What exactly are you trying to do because if I know a little more, I can show you the exact command to do it?

So, let's hear it.

---

### Post by discmaster on 2007-05-28
Hi taurus,

What baskettplayr & I are trying to do is get this latest java installed by following the directions on Sun's website, as well as in the link that FerhatBingol posted; Both say to use chmod.

** Our main issue is this; we are getting the blank white screen when trying to start frostwire, etc. (also running beryl, I understand that complicates things?)

In another thread, I have read that in order to not get the blank white screen, that the very latest vers. of java must be installed.

I know it is a simple process for the "experienced" guys, but us noobs just don't get it! :(

---

### Post by taurus on 2007-05-28
Okay, how about

```
sudo mkdir /usr/java
sudo cp ~/Desktop/jre-6u1-linux-i586.bin /usr/java
cd /usr/java
sudo chmod 755 jre-6u1-linux-i586.bin
sudo ./jre-6u1-linux-i586.bin
sudo update-alternatives --config java
cd /usr/lib/firefox/plugins
sudo ln -s /usr/java/jre1.6.0_01/plugin/i386/ns7/libjavaplugin_oji.so  libjavaplugin_oji.so
```

You should be running the latest version of Sun java and plugins for your firefox.

```
java -version
```

---

### Post by discmaster on 2007-05-28
taurus, I ran the code that you said to. It installed, I rebooted when done...

This is my java vers.
> tr@tr-desktop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
tr@tr-desktop:~$ 


but I still end up with this - the white blank window is "frostwire"...
[[IMG]http://img483.imageshack.us/img483/3623/screenshotblankhu0.png[/IMG]](http://imageshack.us)

has anyone actually gotten this program (frostwire) to work? I am beginning to wonder if it will run with beryl running...

---

### Post by taurus on 2007-05-28
Try switching it to metacity.  Fire up frostwire.  Then, switch it back to emerald or whatever else you are running with beryl.

---

### Post by discmaster on 2007-05-28
Well, I am trying, lol. I googled around a bit, & the closet thing I found was this;
> To test-drive Beryl, first disable Desktop Effects by using the oddball toggle button I described at the end of tip #5. Now open a Terminal window (Applications, Accessories, Terminal) and enter the following command:

sudo gedit /etc/apt/sources.list

Add the following line to the top of the text file that comes up for editing:

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

Save the file and quit. Now back on the command line, issue the following four commands, one at a time:

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get install beryl beryl-manager emerald-themes heliodor beryl-manager

beryl-manager

There should now be a shiny red gem appearing in the notification area (Windows refugees, think "system tray") near the upper right of your screen. Right-clicking that icon gives you several useful options.

Select Window Manager lets you switch among Beryl, Compiz, or Metacity (the default, plain-vanilla window manager for Gnome). Select Window Decorator affects how the frames of windows are drawn. Select Emerald, and you'll get window frames designed with Beryl in mind. (See Emerald Theme Manager, also in the red gem's menu, for more of these.) Select Heliodor, and you'll get plain window borders imported from Metacity.

Selecting Beryl Settings Manager will bring up the labyrinthine configuration dialog box for Beryl. Warning: If you're a settings geek, you will lose a few hours of your life here. Take note of where you can assign functions to the corners of the screen: Select General Options along the top and Shortcuts along the right, and then click the Screen Edges tab. The horribly named 'Initiate Window Picker for All Workspaces' function is the equivalent of Mac OS X's Exposé feature--task-switching nirvana, if you ask me.

If Beryl runs stably and you'd like it enabled every time you log in, select System, Preferences, Sessions. On the Startup Programs tab, click New. Enter beryl-manager in both text-entry fields and click OK. Now click Close.

Is this how you switch it, or is there another way?

EDIT: > There should now be a shiny red gem appearing in the notification area I don't have this to switch between them. I have beryl/emerald in sessions so it automatically runs when I boot...

---

### Post by DougieFresh4U on 2007-05-29
How about like type **frostwire** in terminal and post the output for us to see

---

### Post by esoterica on 2007-05-29
I haven't read any of the posts in here, I just seen this title and wanted to quickly warn you, Java 6, aka version 1.6 is very buggy in Linux and Windows. I'm a Java Programmer so I use the JRE and the JDK and I will tell you first hand, do not go with Java 6 yet, fall back on Java 4 or Java 5 for the JRE , Java 6 will cause you all kinds of unexpected problems, Java 5 will work fine for you and without all the new problems Java 6 will haunt you with!

Very few Java developers are embracing Java 6 yet, so you should not have any problems at all by just sticking with JRE 5.

---

### Post by discmaster on 2007-05-29
> tr@tr-desktop:~$ frostwire
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
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@18d30fb
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
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
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@18d30fb
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
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
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@18d30fb
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
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
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@18d30fb
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
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
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@18d30fb
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
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
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)


@ esoterica - thanks for the info. I will take in under consideration. I guess I could get frostwire to work if I switch beryl off as taurus suggested, as soon as I figure out how..

---

### Post by discmaster on 2007-05-29
UPDATE: **I got frostwire to work**, I don't really know how or what I did exactly...

What I did was this; I typed "beryl" into a terminal window, & it came up with a lot of info., & also I noticed that my "eye candy" went away; For example, the browser windows went "normal", no wiggle, etc. Also, all the windows "stuck" in the corners, tops... So I typed "metacity" in the term. & they became "unstuck".

Why did that happen just by typing beryl in the terminal?
And a more pertinent question, how do I restart beryl now?

I would like to know exactly what I did to cause this, & did I break anything? :o

---

