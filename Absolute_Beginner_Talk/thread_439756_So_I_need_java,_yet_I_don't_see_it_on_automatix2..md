---
title: "So I need java, yet I don't see it on automatix2."
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-05-11
I know it's on automatix1. Why can't I install automatix1? Is java on automatix2 yet I'm not seeing it? I need it to keep frostwire from auto-shutting off.

---

### Post by STREETURCHINE on 2007-05-11
> **Roasted said:**
> I know it's on automatix1. Why can't I install automatix1? Is java on automatix2 yet I'm not seeing it? I need it to keep frostwire from auto-shutting off.

sun java jre is on automatix 2,well it is on mine anyway,
but if you cant find it go to the automatix web site and ask arnieboy he will know what is going on

there is a link in my signature for the automatix forums:)

---

### Post by jfinkels on 2007-05-11
```

sudo aptitude install sun-java6-jre 

```

---

### Post by Roasted on 2007-05-11
jason@jason:~$ sudo aptitude install sun-java6-jre
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
jason@jason:~$ 


It still shuts off. :(

---

### Post by jfinkels on 2007-05-11
> **Roasted said:**
> jason@jason:~$ sudo aptitude install sun-java6-jre
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
jason@jason:~$ 


It still shuts off. :(

Is the multiverse repository enabled?

Do you have java installed already?
```

sudo dpkg -l | grep sun-java

```

What kind of error message do you get when you open azureus from the command line?
```

azureus
```

---

### Post by Roasted on 2007-05-11
jason@jason:~$ sudo dpkg -l | grep sun-java
Password:
ii  sun-java5-bin                              1.5.0-08-0ubuntu1                    Sun Java(TM) Runtime Environment (JRE) 5.0
ii  sun-java5-demo                             1.5.0-08-0ubuntu1                    Sun Java(TM) Development Kit (JDK) 5.0 demos
ii  sun-java5-jdk                              1.5.0-08-0ubuntu1                    Sun Java(TM) Development Kit (JDK) 5.0
ii  sun-java5-jre                              1.5.0-08-0ubuntu1                    Sun Java(TM) Runtime Environment (JRE) 5.0
ii  sun-java5-plugin                           1.5.0-08-0ubuntu1                    The Java(TM) Plug-in, Java SE 5.0
ii  sun-java6-bin                              6-00-0ubuntu1~edgy1                  Sun Java(TM) Runtime Environment (JRE) 6
ii  sun-java6-jre                              6-00-0ubuntu1~edgy1                  Sun Java(TM) Runtime Environment (JRE) 6
ii  sun-java6-plugin                           6-00-0ubuntu1~edgy1                  The Java(TM) Plug-in, Java SE 6
jason@jason:~$ azureus
bash: azureus: command not found
jason@jason:~$ 




Azureus not installed I don't think.

---

### Post by Saphira on 2007-05-11
Automatix is a waste of your time and energy. Refer to these sites for more formalized documentation -- [http://wiki.ubuntu.com](http://wiki.ubuntu.com) [http://ubuntuguide.org](http://ubuntuguide.org) [http://doc.gwos.org](http://doc.gwos.org).

Automatix is known for breaking systems and you'll find that you really don't need it. It may also make upgrading your system later difficult. Also, with Feisty most of the stuff you'll use Automatix to install is already a one click install either via add/remove applications or by referral to one of the above sources.

---

### Post by jfinkels on 2007-05-11
> **Saphira said:**
> Automatix is a waste of your time and energy. Refer to these sites for more formalized documentation -- [http://wiki.ubuntu.com](http://wiki.ubuntu.com) [http://ubuntuguide.org](http://ubuntuguide.org) [http://doc.gwos.org](http://doc.gwos.org).

Automatix is known for breaking systems and you'll find that you really don't need it. It may also make upgrading your system later difficult. Also, with Feisty most of the stuff you'll use Automatix to install is already a one click install either via add/remove applications or by referral to one of the above sources.

Well, if Roasted is more comfortable with Automatix, then let him do what he wants :P

OOhhh I'm so sorry, Roasted, I read azureus instead of Frostwire haha. Woops....

What happens when you open frostwire from the command line? 
```
frostwire
```
Are there any error messages?

---

### Post by lakersforce on 2007-05-11
If you use 7.04 it is already enabled.

---

### Post by bodhi.zazen on 2007-05-11
> **jfinkels said:**
> Well, if Roasted is more comfortable with Automatix, then let him do what he wants :P

LOL

Because as Saphira said, automatix causes system breakage. Automatix is not supported by Ubuntu or the Ubutu forums.

While automatix seems like a simple solution to new users or a quick fix to a seemingly overwhelming problem, under the hood automatix often causes system failure, maybe not immediate, but system failure all the same.

When this happens the situation typically can not be fixed short of re-installing the system.

When this happens, new users do not understand the cause of the failure is automatix and not Ubuntu. So either re-install automatix, or worse, encourage others to use automatix or worse of all, get angry with Ubutnu or perceive Ubuntu as unstable or unusable.

Thus more experienced users, like Saphria, are taking a stand against automatix and you should too.

---

### Post by jfinkels on 2007-05-11
> **bodhi.zazen said:**
> LOL
Don't laugh at me! :P
> 
Thus more experienced users, like Saphria, are taking a stand against automatix and you should too.

Okey dokey, I'll consider this. Thanks for the update. I don't really know anything about Automatix.

---

### Post by zvacet on 2007-05-11
If you still searching for Java it is in synaptic if you have all repositories open.in synaptic type in search box **sun** and pick version of java you want.

---

### Post by mstlyevil on 2007-05-11
> **jfinkels said:**
> Don't laugh at me! :P


Okey dokey, I'll consider this. Thanks for the update. I don't really know anything about Automatix.

I am from the Automatix team and sun-java6-jre is in AX. I also want to mention that millions of people have used Automatix without any problems whatsoever regardless what some may say.

You will find java under codecs and plugins in Automatix.

---

### Post by Mimsy on 2007-05-11
> **bodhi.zazen said:**
> 
Because as Saphira said, automatix causes system breakage. Automatix is not supported by Ubuntu or the Ubutu forums.

While automatix seems like a simple solution to new users or a quick fix to a seemingly overwhelming problem, under the hood automatix often causes system failure, maybe not immediate, but system failure all the same.


I've seen a few forum members here say that, but never seen one of them back that up with a more detailed explanation, or actual data to support their claim. Since I have yet to have any problems with Automatix2 on my system, I would be interested in seeing some actual substance to the statement "Automatix causes system breakage", other than repetitions of "it's not supported" or "it's better for you to do things the hard way from the start"

If it really causes system breakage there must be thousands of examples out there that prove that my own experience is an anomaly. And it surprises me that I haven't seen one held up as support of the claims that automatix is bad for my system, whenever the claim itself is made. At the very least, you should be able to tell me how it does it.

/Mimsy

---

### Post by bodhi.zazen on 2007-05-11
> **mstlyevil said:**
> I am from the Automatix team and sun-java6-jre is in AX. I also want to mention that millions of people have used Automatix without any problems whatsoever regardless what some may say.

You will find java under codecs and plugins in Automatix.

Welcome mstlyevil, always nice to see developers here.

BUT, not to start a flame war, this is what many perceive to be the "problem" with automatix.

All I would ask is that you represent automatix with an even hand.

> millions of people have used Automatix without any problems whatsoever

perhaps. That does come across as an exaggeration however and that does not change the facts about automatix.

[list=number][*]automatix changes the OS, it changes system files so the system is no longer a "clean" ubuntu evnironment.[*]automatix is not an official ubuntu product and maintains a separate repository.[*]While I am sure automatix "works" I am equally sure it can cause breakage as well.[*]There is no easy way to remove automatix and undo the system changes.[/list]

There needs to be a more open discussion from the automatix team surrounding these issues.

FYI  :

> Automatix2 is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to !install a fresh copy of Ubuntu. See also !WorksForMe

> Common Sense: Just because you can, does not mean you should (and especially recommend to others). Think before you do. "Works for me" does not mean it is ok. The latest version of everything is not always useful if you aim for stability.

---

### Post by mstlyevil on 2007-05-11
I don't want to get off topic in a support thread and have it hijacked to a Automatix is good or bad debate but let me answer those four points real quick. After this lets stay on topic in these threads.


> **bodhi.zazen said:**
> perhaps. That does come across as an exaggeration however and that does not change the facts about automatix.

I just want to say on this one I was not exaggerating. AX has at least 2 million users according to our server data.

> **bodhi.zazen said:**
> [list=number][*]automatix changes the OS, it changes system files so the system is no longer a "clean" ubuntu evnironment.[*]automatix is not an official ubuntu product and maintains a separate repository.[*]While I am sure automatix "works" I am equally sure it can cause breakage as well.[*]There is no easy way to remove automatix and undo the system changes.[/list]

[LIST=1]
[*]Automatix backsup all files it changes and has the ability to restore them from AX. Also installing any unsupported software from multiverse and universe results in an Ubuntu system that is not clean. Also I would like to mention that following documentation and changing system files also results in an unclean system. Many users do not make a backup of these files and do not remember what they changed.
[*]Flash, Java, unclean codecs, Mplayer etc are also third party projects yet most Ubuntu users have them. We maintain a seperate repository to ensure only safe packages are installed that will not cause breakage. This means we do not have to rely on third party repos and take the risk of breakge.
[*]Any software can cause breakage. Even supported software can cause breakage. I personally upgraded a fresh Edgy installation with all the AX selections installed and nothing else. I did this three times and not once did an upgrade to Feisty break. We test all the selections for breakage and when a bug is found we are quick to fix it.
[*]First to undo all the changes just use the uninstall option in Automatix to remove all the software and restore backup files.Then uninstall Automatix. There is nothing hard about it at all.
[/LIST]

> **bodhi.zazen said:**
> There needs to be a more open discussion from the automatix team surrounding these issues.

FYI  :

We have been openly discussing these issues. There is a thread in community chat that these very issues were discussed in.

---

### Post by bodhi.zazen on 2007-05-11
> **mstlyevil said:**
> I don't want to get off topic in a support thread and have it hijacked to a Automatix is good or bad debate but let me answer those four points real quick. After this lets stay on topic in these threads.

Well, thanks for you time and thoughtful response. I know you and arnie put a lot of time and effort into automaitx and I admire you for that. 

When you are so close to an issue though it is hard to see potential flaws and when the automatix team fails to recognize those flaws, then support falls to the Ubuntu forums and tension grows.

Please continue you work with automatix, but please do not over sell the product to new users and warn them of potential risks. Again, I feel some responsibility to protect new users from system failure associated with automatix. If the automatix team would take some of that responsibility it would ease tension.

I am not targeting automatix nor do I have a vendetta against automatix.

Roasted0 : Sorry to hijack your thread. If the mods feel this discussion should be moved, I would not object, their call.

---

### Post by crane on 2007-05-11
The way I have read this thread. I hope the original poster gets his problem fixed. But because I am tired of seeing "Help me with Automatx" I will say this.
 If you need help with Automatix go to their forums. If you want help installing Java through apt or anther way ask here.
 Please don't let this thread turn into another debate. Personally I do not remember installing java in 7.04. Maybe a little more info would be helpful. Are you trying to get a plugin working or install Java for development reasons? What errors are you getting making you think you need Java?

---

### Post by Roasted on 2007-05-12
fjason@jason:~$ frostwire
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
expected thread was [Lirc.DispatchThread;@179d854
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
expected thread was [Lirc.DispatchThread;@179d854
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
expected thread was [Lirc.DispatchThread;@179d854
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
expected thread was [Lirc.DispatchThread;@179d854
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
expected thread was [Lirc.DispatchThread;@179d854
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
#  SIGSEGV (0xb) at pc=0xb0e13b70, pid=10552, tid=2964032416
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2eb70]
#
# An error report file with more information is saved as hs_err_pid10552.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 122: 10552 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


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

### Post by jfinkels on 2007-05-12
I don't know what the deal is with your frostwire...perhaps try to install the newer version of java, java 6? Or maybe reinstall your current version? I don't really know.

---

### Post by Roasted on 2007-05-12
I just reinstalled.

Didn't help.

---

### Post by jiminycricket on 2007-05-12
Why aren't you using sun-java6-jre ?  Enable universe and multiverse repos first. [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Then install it.

Then set it to use Sun Java 6

sudo update-alternatives --config java
sudo update-alternatives --config javac

---

### Post by Roasted on 2007-05-12
That link doesn't help me. With the version of Ubuntu I run, which is Edgy, nothing looks the same. In fact, I can't even figure out how to get into the repositories anyway. All I can get to is "software sources" which, I figured would be the same thing, but it looks very different.

---

### Post by taurus on 2007-05-12
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Roasted on 2007-05-12
Taurus. I followed the directions on that link. It still didn't help. Frostwire still shuts off.

Although I want to fix this problem, I'm half tempted to upgrade to Fiesty. Is it worth it? I'd do a fresh install... start from bare minimal again. But I'd still like to tackle this problem.

---

### Post by jonward0690 on 2007-05-12
When i first tried to use linux I started to useing Ubuntu 6.10 it falled to convert me because I could not get frostwire going could'nt get java running eather.Waited for 7.04 and I loved it,it finaly converted me to Linux

---

### Post by Roasted on 2007-05-13
So 7.04 is pretty solid? Should I upgrade, or do a full reinstall? Would it matter? 

I'd still like to solve this problem though, before I upgrade.

---

### Post by jfinkels on 2007-05-13
Have you installed java 6 and tried doing what jiminycricket suggests?

---

### Post by Roasted on 2007-05-13
That's what's interesting. I've done everything suggested to me, yet frostwire still freezes.

---

### Post by jfinkels on 2007-05-13
> **Roasted said:**
> That's what's interesting. I've done everything suggested to me, yet frostwire still freezes.

Hmm, you get EXACTLY the same output when you use java6? That's odd. Have you reinstalled frostwire?```
sudo aptitude reinstall frostwire
```

Do you have the latest version, 4.13.1.7?

---

### Post by Roasted on 2007-05-13
jason@jason:~$ sudo aptitude reinstall frostwire
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REINSTALLED:
  frostwire 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate file for the frostwire package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
jason@jason:~$ 


I have 4.13.1 beta.

---

### Post by jfinkels on 2007-05-13
> **Roasted said:**
> jason@jason:~$ sudo aptitude reinstall frostwire
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REINSTALLED:
  frostwire 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate file for the frostwire package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
jason@jason:~$ 


I have 4.13.1 beta.

Try 'sudo aptitude remove'ing frostwire, then download the .deb from the frostwire website.

---

### Post by Roasted on 2007-05-13
> **jfinkels said:**
> Try 'sudo aptitude remove'ing frostwire, then download the .deb from the frostwire website.

I did that a few days ago and I got a package error.

---

### Post by jfinkels on 2007-05-14
> **Roasted said:**
> I did that a few days ago and I got a package error.

I am truly sorry, friend, but I have no idea what's going on with your computer. Perhaps the fates did not want you to use frostwire. Try gtk-gnutella :D

---

### Post by Sef on 2007-05-14
> I did that a few days ago and I got a package error.

What was the error?  Posting it could help resolve your problem.

---

