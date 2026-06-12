---
title: "help!! azureus suddenly doesn't work!"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by benx009 on 2007-08-03
help!  when i try to start azureus, i get the following error:

```
:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Fri Aug 03 16:51:11 EDT 2007::com.aelitis.azureus.core.networkmanager.VirtualChannelSelector::select::272:
  Caught exception on selector.select() op: Operation not permitted
    NonBlockingReadWriteService$1::runSupport::80,AEThread::run::69
java.io.IOException: Operation not permitted
        at sun.nio.ch.EPollArrayWrapper.epollCtl(Native Method)
        at sun.nio.ch.EPollArrayWrapper.updateRegistrations(EPollArrayWrapper.java:202)
        at sun.nio.ch.EPollArrayWrapper.poll(EPollArrayWrapper.java:183)
        at sun.nio.ch.EPollSelectorImpl.doSelect(EPollSelectorImpl.java:65)
        at sun.nio.ch.SelectorImpl.lockAndDoSelect(SelectorImpl.java:69)
        at sun.nio.ch.SelectorImpl.select(SelectorImpl.java:80)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualChannelSelectorImpl.select(VirtualChannelSelectorImpl.java:446)
        at com.aelitis.azureus.core.networkmanager.VirtualChannelSelector.select(VirtualChannelSelector.java:272)
        at com.aelitis.azureus.core.clientmessageservice.impl.NonBlockingReadWriteService$1.runSupport(NonBlockingReadWriteService.java:80)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=5846, tid=3084217232
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid5846.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

this is weird because azureus was working fine until now.  arggg, i hope i do not have to reinstall java...

---

### Post by splintercellguy on 2007-08-03
Delete ~/.azureus/logs directory I think.

---

### Post by benx009 on 2007-08-03
> **splintercellguy said:**
> Delete ~/.azureus/logs directory I think.

i have no idea how that worked, but i took your advice and azureus runs again!  thanks:)

---

### Post by mgmiller on 2007-08-03
I also suddenly had problems with Azureus and deleting those files would work for a while, then the problem would reoccur.  I also had constant problems with Azureus in a new install of Feisty I did for some one.  I solved the problems finally by installing ktorrent and using it instead of Azureus.  It runs fine in gnome.

---

### Post by benx009 on 2007-08-03
> **mgmiller said:**
> I also suddenly had problems with Azureus and deleting those files would work for a while, then the problem would reoccur.  I also had constant problems with Azureus in a new install of Feisty I did for some one.  I solved the problems finally by installing ktorrent and using it instead of Azureus.  It runs fine in gnome.

yes, perhaps i should take up ktorrent....

---

### Post by Inxsible on 2007-08-03
> **benx009 said:**
> yes, perhaps i should take up ktorrent....

if you dont want a kde app per se(not that it wont work ;) ) you could give [qBittorrent]("http://qbittorrent.sourceforge.net/") a trry. I use it and its great. it offers a lot of features like PEX and DHT etc etc.

---

### Post by kodoku on 2007-08-03
> **Inxsible said:**
> if you dont want a kde app per se(not that it wont work ;) ) you could give [qBittorrent]("http://qbittorrent.sourceforge.net/") a trry. I use it and its great. it offers a lot of features like PEX and DHT etc etc.

lol. qBitTorrent is written in Qt4, which makes it more of a KDE app than Gnome.

---

### Post by Inxsible on 2007-08-03
> **kodoku said:**
> lol. qBitTorrent is written in Qt4, which makes it more of a KDE app than Gnome.

ummm..not really, it doesn download a bunch of kde packages which is a good thing. using qt as a toolkit doesnt make it kde
Quote from wikipedia

> Qt is a [cross-platform]("http://en.wikipedia.org/wiki/Cross-platform") application development framework, widely used for the development of [GUI]("http://en.wikipedia.org/wiki/Graphical_user_interface") programs, and, since the release of Qt 4, also used for developing non-GUI programs such as console tools and servers. Qt is most notably used in [KDE]("http://en.wikipedia.org/wiki/KDE"), Agreed its most notably used to build KDE apps, but that does not mean it cant be used to build other apps. Also I never said qBittorrent was a Gnome app :)

---

### Post by jackmc on 2007-08-03
I got sick of azureus issues and switched to deluge. Far less features (which in this case is a plus!) and faster downloads out of the box :)

---

### Post by Crube on 2007-08-14
This should help. If you still want to use Azureus

```
Command line fix:

sudo wget http://superb-west.dl.sourceforge.net/sourceforge/azureus/Azureus2.5.0.0.jar

sudo mv Azureus2.5.0.0.jar /usr/share/java/Azureus2.jar
```

---

### Post by jingo811 on 2007-08-14
Azureus/Java also just crash on me whenever I start the program never happened during the 2 months testing before.  So I just uninstalled it for good and tried Deluge it's nice :) Ktorrent also good but it has some specific minor problems that annoyed me.  Both are functional though.

---

### Post by netimen on 2007-08-17
> **benx009 said:**
> i have no idea how that worked, but i took your advice and azureus runs again!  thanks:)
For me it also has solved the problem!

---

