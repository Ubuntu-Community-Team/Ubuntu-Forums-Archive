---
title: "Which Java is right Java?"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by Craftycorner on 2006-12-09
In order to obtain live help, Ebay says I must run Java.  They offer a download page with several 'flavors'.  They are 

Linux RPM (self-extracting file)
Linux (self-extracting file)
Linux x64 (see below Note)
Linux x64 RPM (see below Note)

I heard that Dapper and RPM don't like each other alot, so I should avoid them, but how do I install these/this bugger?

---

### Post by Shed on 2006-12-09
> **Craftycorner said:**
> In order to obtain live help, Ebay says I must run Java.  They offer a download page with several 'flavors'.  They are 

Linux RPM (self-extracting file)
Linux (self-extracting file)
Linux x64 (see below Note)
Linux x64 RPM (see below Note)

I heard that Dapper and RPM don't like each other alot, so I should avoid them, but how do I install these/this bugger?

Follow [guide](https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages) to enable universe and multiverse.
Update Synaptic.
Search Synaptic for Java and install (from memory I think it's sun-java5-java or similar).

---

### Post by meng on 2006-12-09
After enabling extra repositories:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by igknighted on 2006-12-09
the package you want is 'sun-java5-jre'.  It can be found in synaptic (or adept if you use kubuntu) once all repositories are enabled.

---

