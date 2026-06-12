---
title: "Firefox segfaults after upgrade"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by KevlarGurra on 2007-03-02
Hi

My firefox won't start after the latest update (to 2.0.0.2 I think). When I try to run it from the shell, it says something about a segmentation fault. How can I fix this?

---

### Post by KevlarGurra on 2007-03-03
Would it be possible to revert to the previous version or something? How would I do that?
And am I the only one who have experienced this...?

---

### Post by KevlarGurra on 2007-03-04
I fixed it by reverting to the previous version of Firefox... It's really strange, is the new version working for everyone but me?

---

### Post by BrowneR on 2007-03-04
i am having the same problems since the 2.0.0.2 update however only sporadically.

most of the time it works however some things seem to trip it off. i'm not sure what is triggering this... what extensions are you guys using?

i am using:

fasterfox
greasemonky
mplayer-plugin
downloadThemAll!

---

### Post by KevlarGurra on 2007-03-04
> **BrowneR said:**
> i am having the same problems since the 2.0.0.2 update however only sporadically.

most of the time it works however some things seem to trip it off. i'm not sure what is triggering this... what extensions are you guys using?

i am using:

fasterfox
greasemonky
mplayer-plugin
downloadThemAll!

I'm using:
Adblock
Download Statusbar
Fasterfox
Firebug
Flashblock
Forecastfox Enhanced
MediaPlayerConnectivity
SEO For Firefox
Split Browser
Swedish Dictionary
TV-Guide (Swedish)
Web Developer

I don't think it's because of the extensions though. After the upgrade, I noticed that Eclipse would crash very time it showed an info box and after some research I fond that Eclipse complained about a .so file residing in the Firefox directory. Apparently, Eclipse used that file to draw the information box, and the upgrade somehow broke that file...

---

### Post by BrowneR on 2007-03-04
hmm i guess we should file a bugreport on launchpad as its not going to get noticed here...

i have been searching through [launchpad]("https://launchpad.net/ubuntu/+bugs") looking for similar bugs but its hard to tell...

does anyone know how i can get a backtrace of the crash using the debug package?

---

### Post by BrowneR on 2007-03-05
right i have found out how to get a backtrace from the wiki and have installed the firefox 2.0.0.2 debug package however i cannot currently get the thing to crash!

i will post a link to the launchpad report when i have submitted it.

---

