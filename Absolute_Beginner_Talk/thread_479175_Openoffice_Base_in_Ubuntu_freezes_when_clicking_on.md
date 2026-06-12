---
title: "Openoffice Base in Ubuntu freezes when clicking on Tables"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by goldemaire on 2007-06-20
Hi,

I've got a trouble on bringing data into OOo base. I have successfully created a new database but the problem is that I could not open tables, the application just hangs up and asks to forced quit after clicking "tables".

Please Help!!!!!:confused:

---

### Post by bapoumba on 2007-06-20
Thread moved to "Absolute Beginner Talk" support forum.

---

### Post by Hagar Delest on 2007-06-20
I'm not used to Base but it may be a problem with the Ubuntu version of OOo.

Wait for a while and if there is no other answer, try to remove the Ubuntu version and install the official version, it's more stable, see here : [[Ubuntu] Installing OOo on Debian and Co.]("http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759")

---

### Post by steve.horsley on 2007-06-20
I wonder if it's the version of java that's on your machine. OOo doesn't seem to get on too well with the FLOSS java that gets installed by default. Try installing Sun's java JRE.

---

### Post by goldemaire on 2007-06-20
> **steve.horsley said:**
> I wonder if it's the version of java that's on your machine. OOo doesn't seem to get on too well with the FLOSS java that gets installed by default. Try installing Sun's java JRE.


My OOo is now using JRE..just replaced the default java thing. Still having the same situation on Base...:(

---

### Post by tjfitz on 2008-02-04
I have this same problem with Open Office Base. I created a new database with the wizard, but as soon as I tried to set up tables (or do ANYTHING to it), it froze up, and I had to force quit.  I installed all the "suggested" database drivers, as well as the Sun Java JRE, and it still did the same thing.  I am actually using Debian Etch with OOo v. 2.0

---

### Post by Hagar Delest on 2008-02-04
Then, install the official version, see updated tutorial here: install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by tjfitz on 2008-02-04
There's no way to fix the Debian version? :(

---

### Post by tjfitz on 2008-02-04
Ok, I removed the Debian packages, and installed the tarred/gzipped .deb's from the openoffice.org site.  I opened Base, and it is much more responsive, but it's giving me an error about my JRE being defective, and to please select another.  I reinstalled the Sun Java packages.  Do I need to get rid of those Debian-rolled packages too and get it straight from Sun?

---

### Post by tjfitz on 2008-02-04
Holy cow, that is weird!  I went back into the options again to see if there was something in the "java" page I overlooked.  Sure enough, the little circle next to Sun Java JRE wasn't filled in...even though it is the only one there.  I clicked the circle to select it, and now it is working, but it's very strange that OOo detected it and listed it but didn't automatically select it! :confused:

---

### Post by Hagar Delest on 2008-02-05
Yes, it happens sometimes on Linux, don't really know why neither.

---

