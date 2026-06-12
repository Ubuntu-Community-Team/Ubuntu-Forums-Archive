---
title: "Azureus Vuze - messed up interface"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by peterbuldge on 2007-11-11
I'm running Kubuntu Gutsy.

I've search around and I can't find any other reference to this problem.  Whether I install Azureus from a deb or from the sourceforge tarball, the interface always looks incomplete. 

This happened in Feisty too.  I've never see Azureus Vuze look Normal in Kubuntu.  I have the latest Sun Java Runtime installed from the repos.  Vuze looks fine for me in XP... and everytime I see a pic of it running in Ubuntu or Kubuntu it looks fine as well.  Does anybody have any idea what the problem is here?

---

### Post by ohzopants on 2007-11-13
Try running it from the terminal and see if there are any errors.

Post them here if there are any, maybe I (or someone else) can help.

---

### Post by peterbuldge on 2007-11-13
I can't see anything that looks weird myself...but either way...

Starting Azureus...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Java exec found in PATH. Verifying...
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/home/peterbul
dge/apps/azureus" -Dazureus.install.path="/home/peterbuldge/apps/azureus" -Dazur
eus.script="/home/peterbuldge/apps/azureus/azureus" -Dazureus.script.version=2 o
rg.gudy.azureus2.ui.swt.Main
changeLocale: *Default Language* != English (United States). Searching without c
ountry..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US)
, using 'English (default)'
Locale Initializing took 662ms
   Core: 25ms for Loading Plugin : azemp
   Core: 25ms for Loading Plugin : azupnpav
   Core: 53ms for Loading Plugin : azrating
   Core: 51ms for Loading Plugin : azplugins
   Core: 178ms for Loading Plugin : Built In
   Core: 375ms for Initializing Global Torrent Manager
   Core: 25ms for Initializing Plugin: Embedded Media Player
   Core: 102ms for Initializing Plugin: UPnP Media Server
   Core: 26ms for Initializing Plugin: Tracker Static Pages
   Core: 51ms for Initializing Plugin: Tracker Static Pages
   Core: 25ms for Initializing Plugin: PluginUpdate
   Core: 25ms for Initializing Plugin: DHT
   Core: 26ms for Initializing Plugin: DHT Tracker
   Core: 25ms for Initializing Plugin: azplatform2
Core Initializing took 1238ms
GUI Initializing took 76ms
DEBUG::Wed Nov 14 03:36:47 GMT 2007  ExternalStimulus debug
skin init took 1874ms
   Core: 2253ms for Initializing Plugin: azlocaltracker
createWindow init took 203ms
skin layout took 440ms
skin widgets init took 423ms
shell.open took 655ms
processStartupDMS took 6ms
psDMS 28ms

---

### Post by GTvulse on 2007-11-17
What you see is by design. That's the "Advanced Vuze" Interface. For instructions to set Azureus to use the "Classic" interface, see this post:

[http://ubuntuforums.org/showpost.php?p=3250622&postcount=3](http://ubuntuforums.org/showpost.php?p=3250622&postcount=3)

---

### Post by gerix76 on 2008-01-07
> **dradul said:**
> What you see is by design. That's the "Advanced Vuze" Interface.

I was using Ubuntu before switching to Kubuntu. On Ubuntu, Vuze looks just fine, on Kubuntu -- just as same as in the picture in the first post.

---

### Post by srt4lifez on 2008-05-22
anyone find a solution to this problem? ive seen this issue in opensuse 10.3 and just now installed kubuntu 8.04 and its doing this aswell... driving me insane...

ok, noticed if i run vuze as root the interface looks fine, if i run it as a user its all grey like that... how do i fix this?

---

### Post by GTvulse on 2008-05-23
Have you installed the gtk-qt-engine/gtk-qt-engine-kde4 to integrate GTK+ into KDE?

---

### Post by srt4lifez on 2008-05-24
yeah, that package seems to be installed.

---

