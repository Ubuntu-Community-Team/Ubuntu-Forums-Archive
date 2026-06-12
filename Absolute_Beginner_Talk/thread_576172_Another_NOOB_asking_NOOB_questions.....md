---
title: "Another NOOB asking NOOB questions...."
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Difranco1911 on 2007-10-14
It's been sometime since I've attempted using Linux... tried Slackware and Redhat back in 2002.   Since then I've been mainly been a Windows fella through and through.

Many Applications I've switched over the last year and I really enjoy and use most often:

Open Office
Juice Podcast Receiver
Thunderbird
Firefox
JAlbum

I'd like to switch to Ubuntu however my concerns:

Cellphone -- Sony Walkman W710i >> I like to be able upload my MP3's, wallpapers, Update my phone list through my PC.  It connects via USB, is there an app that can do this on the Linux side?

GPS Unit -- Garmin GPSMAP 60CSx >>  I love Geocaching so it's a must that I be able to upload and download waypoints etc.   Is there a similar application such as GSAK as well.

PDA -- I currently have a Windows Mobile IPaq that runs Cachemate for my Geocaching Adventures.  Linux alternative?

Camera --  I have a Canon Powershot A560 that I've recently purchased; Will I be able to get my camera to work with Ubuntu?

Well those are my core concerns...  your thoughts and insight are appreciated.

---

### Post by defrex on 2007-10-14
The Camera I can guarantee. I don't know much about software for GSP units are PDAs, but maybe someone else can help you with that. As for the phone, I don't know about that model specifically, but I can tell you that I had a very good experience using a Sony K790 under Linux. It automounted fine, was recognized as a cell, and I could alter all the files and  unload the images and whatnot.

Hopefully that was helpful.

---

### Post by Difranco1911 on 2007-10-14
Thanks... I will work with the Phone but the GPS Unit would be a deal breaker for me.  Keep the comments coming.

---

### Post by conehead77 on 2007-10-14
threads about gps:
[http://ubuntuforums.org/showthread.php?t=219463](http://ubuntuforums.org/showthread.php?t=219463)
[http://ubuntuforums.org/showthread.php?t=516483](http://ubuntuforums.org/showthread.php?t=516483)

I hope they help.

These are working GPS Units (taken from the german Ubuntu Wiki):
NaviLock NL-202U
Holux GM210 USB (Modul pl2303)
iGPS-M Pro USB (wird als CP2101 erkannt, Modul cp2101, läuft sofort als /dev/ttyUSB0)
QSTARZ BT-Q818

---

### Post by p_quarles on 2007-10-14
> **Difranco1911 said:**
> Thanks... I will work with the Phone but the GPS Unit would be a deal breaker for me.  Keep the comments coming.
I think the best advice for anyone in your position is to set up a dual boot system. The GPS device probably won't work with any Linux-native programs, but it's a good bet that you'll be able to get the Windows software running either with Wine or with Virtualbox. Ultimately, the only way to know is to try, and by dual-booting you'll be able to tweak your Linux setup when you have the time, while still keeping Windows around for when you need everything to work the way it used to. 

Ubuntu does not yet work perfectly for everyone's needs. That said, if you can spare the time and effort to configure things, it's usually possible to get most things working. Dual-booting is a pretty painless and non-risky way of going about this.

---

### Post by Difranco1911 on 2007-10-15
Its too bad there isn't some sort of Open Source GPS Developers out there as Garmin has released all kinds of information for developing for their units

[http://www8.garmin.com/support/commProtocol.html](http://www8.garmin.com/support/commProtocol.html)

---

### Post by p_quarles on 2007-10-15
> **Difranco1911 said:**
> Its too bad there isn't some sort of Open Source GPS Developers out there as Garmin has released all kinds of information for developing for their units

[http://www8.garmin.com/support/commProtocol.html](http://www8.garmin.com/support/commProtocol.html)
Awesome. Just did a search for Garmin packages in the Ubuntu repositories and got this:
```
gpsbabel - GPS file conversion plus transfer to/from GPS units
gpsdrive - Car navigation system
gpsman - A GPS manager
gpstrans - communicate with a Garmin Global Positioning System receiver
kflog - Flight planner and logger for glider pilots
```
You didn't mention that Garmin was open-source friendly before :)  It really is true that once hardware vendors release their specs, the GNU/Linux devs are quick to make working applications.

---

### Post by Difranco1911 on 2007-10-15
I didn't know before just doing a little research, I think the SDK for Garmin is a relatively new thing for them.

---

