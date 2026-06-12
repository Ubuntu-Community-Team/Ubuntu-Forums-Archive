---
title: "Amarok + Frostwire troubles"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by SexyLexie on 2007-06-20
Hi guys. I installed ubuntu for the first time today and it's awesome, but I'm having  a little trouble getting Amarok to work properly. Every time I try to drag a song onto the playlist, I get this:

[IMG]http://i76.photobucket.com/albums/j13/Wyrd07/ohnoes.png[/IMG]

I have done everything recommended in [this thread](http://ubuntuforums.org/showthread.php?t=413624), (other than DVD playback) but it doesn't seem to be helping. 

Also, I have installed Frostwire, but when I open it all that comes up is a blank grey window. 

Does anyone know how I can fix either of these?

---

### Post by Betta on 2007-06-20
Under add/Remove Applications > Sound/Video install "gxine" and "Xine extra plugins". That's what I did to get mine to work.

-Betta

---

### Post by SexyLexie on 2007-06-20
Ah! Many thanks for the swift reply Betta, it's working perfectly now.
Amarok, that is. Frostwire is still not working.

---

### Post by mahiyar on 2007-06-20
Open a empty file in gedit or whatever. Put in the following lines

#!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/frostwire

Save as something like frostrun.sh or whatever, on your desktop or wherever you like.

Make it executable like >> chmod +X [I]filename
[/I]
And run it.

---

### Post by SexyLexie on 2007-06-20
Mahiyar, could you go into more detail as to how one would "make it executable"? Sorry, I'm very new at this.

---

### Post by mahiyar on 2007-06-21
from the command line or terminal go into the directory where you have created the *filename.sh *file. You can check the directory where you are in using the >>pwd command. Once in the directory use this command >>sudo chmod +x *filename.sh  *where *filename.sh  *is the file which you have created.

---

### Post by SexyLexie on 2007-06-21
it's still not working! I did exactly what you said but al I see is this:
[IMG]http://i76.photobucket.com/albums/j13/Wyrd07/frostwirenoworky.png[/IMG]

---

### Post by mahiyar on 2007-06-22
I'am stumped. Actually this problem arises when you use beryl/compiz. The only other problem is java version, to check the java version, in the terminal type >>sudo java --version from the terminal. Frostwire needs version 1.5 or more. Another option is to run frostwire(>>frostwire ) from the terminal and see for any error reports in the terminal itself.
 
If you are running beryl or compiz by any chance (viz enhanced desktop effects), come out of it and then see if frostwire starts.

---

### Post by SexyLexie on 2007-06-22
I'm not using beryl, but I was using desktop effects. I turned them off, but it didn't help. CHecked java, am running 1.6. I ran frostwire through terminal, and got this:

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
expected thread was [Lirc.DispatchThread;@2b249
current thread is Thread[main,5,main]

I sent it to [email]bugs@frostwire.com[/email], hopefully they will be able to help.

---

### Post by mahiyar on 2007-06-22
Are you runnung 64 bit version of Ubuntu?

---

### Post by SexyLexie on 2007-06-22
Um...maybe, I don't know. I burned a live disk from [here](http://www.ubuntu.com/getubuntu/download)

---

### Post by esc1 on 2007-07-05
> **mahiyar said:**
> Open a empty file in gedit or whatever. Put in the following lines

#!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/frostwire

Save as something like frostrun.sh or whatever, on your desktop or wherever you like.

Make it executable like >> chmod +X [I]filename
[/I]
And run it.

This worked for me.  Thank you very much.  I assume I can do the same thing for Azureus.  It keeps crashing on me as well.

---

