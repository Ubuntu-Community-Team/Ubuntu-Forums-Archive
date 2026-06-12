---
title: "Anything like Streets and Trips?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by HDave on 2007-12-02
I am in the process of switching from Windows to Ubuntu.  Was wondering if there was any equivalent to MS Streets and Trips program.

I need an **offline** travel/desktop mapping program to give me directions.

GPS is not needed....though it would be a plus.

Does google maps have a way to work offline? Don't think so....

Thanks.

---

### Post by Kyran on 2007-12-02
Well, Google Earth saves images in cache for later use, so, if you have internet access for a limited time you should be able to download an entire region for later offline use. :D There is a setting in its preferences to increase cache size.

---

### Post by HDave on 2007-12-03
Any way to download all of the USA in Google Earth automatically and leave out the satellite imagery?

---

### Post by HDave on 2007-12-05
*bump*

Anyone??

---

### Post by iheartubuntu on 2008-03-25
I too am looking for a linux equiv of MS Streets and Trips. No GPS needed.

---

### Post by wesley_of_course on 2008-03-25
Evening people  , got to looking around and found   " gpsbabel "  in synaptic.

     Sounds promising , 
   ```
GPSBabel converts waypoints, tracks, and routes from one format to
another, whether that format is a common mapping format like Delorme,
Streets and Trips, or even a serial upload or download to a GPS unit
such as those from Garmin and Magellan
```           Good luck !

---

### Post by HDave on 2008-03-28
GPSBabel will convert the waypoints and route, but not the map data itself.

While I have purchased Streets and Trips from MS, there is no program that I can find that can read or convert its map files (which I believe are in some proprietary .dat format -- what a shock!).

The best source of (convertable) map files that I have found are available from the [open street maps]("http://www.openstreetmap.org/") (OSM) project.  Best of all, OSM maps are free as in freedom.  They are also fairly accurate...not as good as S&T, but getting there.

Apparently it is possible to download the entire global openstreetmap database into one local file on your harddrive with a simple wget command.

So the question at this point is:   Is there a good Linux based, street mapping program that can display and create routes based on OSM maps? 

Here are some programs I tried:

GoogleEarth -- Apparently there is a way to convert OSM maps into the KML files that GE needs, but I have not been able to get that to work.  If anyone has any ideas, this is probably the best approach.

RoadMap -- This program looked promising, but development has halted apparently -- and there is no .deb package...you must compile from source.

Traveling Salesman -- Looks promising, but it a brand new project and is not ready to be used.

RoadNAV -- This is the only solution that works at all.  The program is archaic, buggy, and slow, but it works.  However, it seems it will only use the frequently incorrect TIGER data for the US.  The OSM maps can only be used outside the USA...sigh.

FreeMap -- There are forks of the RoadMap project but they are isolated to south England and Israel.

GPSDrive -- This may be the new contender.  Apparently there is a way to make this application use OSM files, but it isn't simple...and their website says that GPSDrive is bitmap based, not vector based.  Perhaps that is changing?

For now, I plan to dig into GPSDrive/OSM support...and to look for a way to convert OSM into KML.  If anybody knows how to do either of these two things, please speak up!!!!

---

### Post by wesley_of_course on 2008-04-04
KML Manager  , have you seen it ?   Sounds like a file converter of sorts.

Heres the link ; [http://www.mchme.com/](http://www.mchme.com/)    Good luck

---

