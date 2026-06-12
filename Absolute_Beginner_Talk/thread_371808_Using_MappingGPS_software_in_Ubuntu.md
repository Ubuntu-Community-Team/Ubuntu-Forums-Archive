---
title: "Using Mapping/GPS software in Ubuntu"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by edwardLS on 2007-02-27
I am running Ubuntu (Dapper) on a Laptop as half of a dual-boot system with XP being the other half.  I mostly use the laptop for vacation/travel to store digital photos from my camera, and for Mapping/GPS software.  In particular I use Microsoft (sorry) Streets & Trip, DeLorme Street Atlas, and National Geographic TrailSmart.  

My question:  Are there any equivalent applications for Linux, or has anyone attempted installing these in linux using Wine?  I have not yet ventured into Wine, but would be willing to give it a go if anyone has had success in this area.

---

### Post by amaroKer on 2007-02-27
A search for "GPS" in "Add/Remove Applications" yields "GPSDrive", which may or may not be what you're looking for.  I'm not sure what any of the programs that you've been using do, but Google Earth has the capability to connect to some GPS units as well, and is an amazingly flexible GIS.  Try that out.  Sorry, that's all I got for ya now.

Logan

---

### Post by ramjet_1953 on 2007-02-27
Check out this site.

[http://www.gpsdrive.cc/](http://www.gpsdrive.cc/)

If the software is what you are after, it can be dowloaded from Synaptic, as it is in the repositories and has been compiled for Ubuntu.

Regards,
Roger 8)

---

### Post by tgalati4 on 2007-03-29
GPSdrive  works well by itself.  I have also loaded Kismet and it works on Dapper LTS.  I am having trouble getting mysql to load (crashing innodb--nothing on the forums).  This is needed to pass the detected AP's as a waypoint database that GPSdrive can display.  I'm using a Microsoft (double sorry) usb GPS (Pharos GPS-360, SirFII chip).  It works well with GPSdrive.

I have to tell you:

I have a powerbook with Tiger 10.4.8 and I installed KisMac--a kismet/gpsdrive clone.  It works really well.  No mysql to install.  AP's get logged automatically.  You can map GPS tracks (every 10 seconds works well for warwalking).  Display AP's in color code by strength or protocol.  Get details by clicking the specific AP, get coordinates by clicking on the AP flag on the map.  Overall a really nice bundle.  It also has a speech processor (as part of the Tiger system), I have not used it, but I imagine it works.

I like open source software, but I have to admit, KisMac is a sweet package that runs with little or no configuration.

Under Linux:  GPSdrive, Kismet, Mysql, Festival and hope it all works!  Each program by itself has issues with different versions of Ubuntu.  I know since I have encountered many of them.  Of course when it all works, it works well and is scaleable.  Imagine a billion waypoints?  And detailed maps of the entire earth?

Good luck.

---

