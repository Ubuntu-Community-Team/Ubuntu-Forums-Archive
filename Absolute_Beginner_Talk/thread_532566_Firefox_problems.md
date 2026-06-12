---
title: "Firefox problems"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by kbar78 on 2007-08-22
Hello, I've just started having issues with firefox greying out (not responding) spontaneously when I browse the web.  This problem seems to be worst on wikipedia, or browsing sites with a lot of graphics to load, such as the NY Mets website.  All the java and flash applets seem to load correctly, but unexpectedly the screen will fade in and out of grey at about 30 second intervals. 

Also, every time I start firefox, it gives me the option to start a new session or resume my last one, regardless of if i had to force the browser to quit or not. 

This dosen't happen with any other browser, and the terminal dosen't show any errors when launching firefox.


FIrefox is 2.0.0.6, using the Noia Extreme skin and FoxyTunes, both of wich are up to date.


anyone else been having this problem, or at least know what might be causing firefox to freeze up?


thanks a lot

---

### Post by kerry_s on 2007-08-22
try the sites with out the extensions/themes, if it works than you know 1 of those is the culprit.

firefox -ProfileManager
or
firefox -safe-mode

for a clean test.

---

