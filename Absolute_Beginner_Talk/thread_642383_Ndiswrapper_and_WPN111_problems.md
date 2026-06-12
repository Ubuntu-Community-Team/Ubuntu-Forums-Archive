---
title: "Ndiswrapper and WPN111 problems"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by edsmaffs on 2007-12-16
Hello.
I am getting very irritated with Linux. My WPN111 adapter STILL doesn't work. :(
But, I'm not giving up yet!

Problem so far: I've installed the drivers in ndiswrapper, but modprobe doesn't work. Or does it? I'm not sure.

When I type in *sudo modprobe ndiswrapper*, I get a lovely polite message saying **FATAL ERROR: Module ndiswrapper does not exist** (not sure if it's exactly worded like that). 

:(
So, does anyone know why Linux and ndiswrapper hate me?

---

### Post by gn2 on 2007-12-16
This lot should get you going :)

[http://ubuntuforums.org/showthread.php?t=414023&highlight=WPN111](http://ubuntuforums.org/showthread.php?t=414023&highlight=WPN111)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by edsmaffs on 2007-12-16
Aha - a known bug!
:(
Still not good!
OK. Can someone lead me through step by step how to manually compile ndiswrapper? (It says installing from the deb package gets you this horrible error.) And how do I get the utils and the gtk (don't know what this is) onto Ubuntu if the deb packages don't work?

---

### Post by Erwin Criddle on 2008-03-05
Visit this link: [http://ubuntuforums.org/showthread.php?t=652910]("http://ubuntuforums.org/showthread.php?t=652910")

It's a complete tutorial on how to compile ndiswrapper and configure the WPN111 wireless adapter.

---

