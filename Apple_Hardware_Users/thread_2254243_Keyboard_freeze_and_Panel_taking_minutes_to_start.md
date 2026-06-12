---
title: "Keyboard freeze and Panel taking minutes to start"
date: 2014-11-25
forum: Apple Hardware Users
---

### Post by vsanchez1961 on 2014-11-25
Hi, 

I have been using Kubuntu 14.10 with Plasma5. It all worked fine, but something begin happening yesterday I cannot remember anything I did to cause it and have been unable to solve it.

Suddendly, when starting a session the Panel (the strip in the bottom of the desktop) takes about 5 minutes to show up. Other programs like amarok and ktorrent take minutes to start. (The desktop itself takes 15secs more to start than before).

Another thing that started happening was that pressing any of the function keys to control volume, brightness, etc freezes the keyboard until i reboot. 

Probably both things are related. Things I have tried:

1. Using "xev" i can see that presing a function key does not generate a KeyPress event.. "showkey" does show a key press, so it is probably something trapping the keys before it gets to X (?)

2. I renamed ".kde" to another name to start with a clean configuration but it was the same...

Any suggestions of things to test? What takes control of the special function keys in KDE/X?

 Thanks

---

### Post by vsanchez1961 on 2014-11-27
When trying to look at the keyboard configuration using systemsettings5, I get a delay of a couple of minutes and the following message when if finaly comes up:

Failed to get dbus path for component  "KDE Keyboard Layout Switcher" QDBusError("org.freedesk
top.DBus.Error.NoReply", "Did not receive a reply. Possible causes include: the remote applica
tion did not send a reply, the message bus security policy blocked the reply, the reply timeou
t expired, or the network connection was broken.")

Any ideas??

---

### Post by vsanchez1961 on 2014-11-27
Hi, I managed to solve the problem. There was something wrong in the file .config/kglobalshortcutsrc (there was also a *.lock file, which is not there anymore) used by kglobalaccel5 to find global accelerate keys.  unfortunately I just erased them so I do not exactly what was wrong with them.. Now everything is back to normal...

---

