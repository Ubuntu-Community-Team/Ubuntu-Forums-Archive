---
title: "Sunbird &amp; Lightning ext for PPC"
date: 2007-06-12
forum: Apple PPC Users
---

### Post by STUMPOFWAR on 2007-06-12
I am trying to get one or the other to work with little success. I installed sunbird following the directions posted on the forums. The sunbird icon is listed in my drop downs but when I click on it nothing happens.

When I try to get Lightning installed in Thunderbird I get a "linux-PPC-G3" not supported error message.

What options do I have?

---

### Post by ssam on 2007-06-13
which instructions did you follow?

if it involved downloading a prebuilt package, are you sure you got a powerpc version and not an x86 version?

---

### Post by STUMPOFWAR on 2007-06-14
I followed the generic "how to" thread I found through the forum search........I didn't think that Sunbird was architecture dependent......where is a PPC package located?

and thanx for the response.......


Shawn

---

### Post by sulobanks on 2007-06-15
You can download the sunbird source code and compile it yourself.  I've never compiled mozilla software before, so I'm not sure how involved it is.  I plan on doing so myself in the next week.  I'm just buried in projects atm.

Or you could compile thunderbird 2 from source and and then use the lightning extension.

---

### Post by j.c.sackett on 2007-10-20
Hi--

I've been trying to build Sunbird from source on a powerbook g4 running Feisty. Everything is up to date, with the possible exception of gtk. When I run configure, it errors out with:

> 
checking for gtk+-2.0 >= 1.3.7... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 1.3.7) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


I've done a re-install of libgtk2.0, but I can't seem to find it anywhere beyond documentation. Everywhere in the usual lib locations I only find 1.2. Is 2.0 not available for power pc? Or is there something else I'm missing?

---

### Post by ubuntubrian on 2007-10-20
Are you following the Mozilla build instructions? I finally got Sunbird Installed after days and days and then following an update it quit working. It shouldn't be so hard and building from source using Moz is a nightmare!
I installed the extension Lightning for Sunbird. Download from the extensions site for Thunderbird-don't click on the install now button. It won't work. Save the link to your desktop and then install from Thunderbird with the extensions manager. It works great and is architecture independent.

---

