---
title: "Can't install Firefox Add-ons"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-12
I was trying to install Firefox add-ons from the official site, but there was an error message (attached). Also, while installing, it says that the Add-on is "Unsigned."

What do I do to fix this?

---

### Post by aysiu on 2007-04-12
Sounds as if something's wrong with the add-on itself. Maybe report a bug to the ForecastFox developer?

---

### Post by Hishgraphics on 2007-04-12
Is it just that one add-on or all of them?

Very rarely I get that error message for all the add-ons. I coulnd't download and install any of them. I discover when I restart Firefox, the error disappears and I can install add-ons again. No idea why this is, though.

---

### Post by wersdaluv on 2007-04-12
It happens to all add-ons

---

### Post by aysiu on 2007-04-12
I Googled your error and got this:
[http://forums.mozillazine.org/viewtopic.php?t=490833](http://forums.mozillazine.org/viewtopic.php?t=490833)

---

### Post by wersdaluv on 2007-04-13
> Linux

Close the application completely and make sure that it is not running in the background. Open the terminal and execute cd (program directory) then execute:

    * (Firefox) ./firefox -profilemanager
    * (Mozilla Suite) ./mozilla -profilemanager
    * (Thunderbird) ./thunderbird -profilemanager 

Alternately, in a terminal type the path/to/firefox-mozilla-thunderbird -profilemanager 

What's the program directory for Firefox? Until now, this confuses me. Is it /home/var/lib/mozilla-firefox?

---

### Post by aysiu on 2007-04-13
Press Alt-F2 and type ```
firefox --profilemanager
``` If you're trying to get a fresh profile, this will help: [HowTo Get Rid of a Corrupt Firefox Profile (and keep the bookmarks)](http://ubuntuforums.org/showthread.php?t=103930&highlight=firefox+corrupt)

---

### Post by wersdaluv on 2007-04-13
Thanks, aysiu!

It works now.

I'm just wondering. When you say Firefox's program directory, is it /home/var/lib/mozilla-firefox?

---

