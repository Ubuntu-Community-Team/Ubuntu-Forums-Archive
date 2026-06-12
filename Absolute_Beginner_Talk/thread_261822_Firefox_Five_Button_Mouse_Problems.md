---
title: "Firefox Five Button Mouse Problems"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by spadewarrior on 2006-09-20
Is it possible to change the way my mouse buttons work in Firefox? I'm using version 1.5.0.7. (upgraded using the deb file).

The middle button no longer closes tabs in this version. Instead it seems to load a seemingly random link somewhere from a previous page.

Also, the forward and back buttons don't work as they should (they didn't work on the version bundled with Ubuntu either, but the middle button did. 

i'm using Dapper. 


I haven't been able to find anything useful from google searches. Is the best bet to alter something in Firefox (be it with an extension or about:config) or would it be better to alter a config file somewhere in Ubuntu so that I could then also the mouse buttons to move back and forth through directories?

---

### Post by Tanath on 2006-09-20
Open about:config in Firefox and check this:

middlemouse.contentLoadURL

Mine is the default, and middle-click closes the tab.

---

### Post by Stew2 on 2006-09-20
Check out [this section]("http://ubuntuguide.org/wiki/Dapper#Activate_side-mouse-buttons_in_FireFox") of the Ubuntu Dapper guide. If you have one of the listed mice, this will get the forward/back buttons to work.  I have a logitech MX518 gaming mouse and the forward/back buttons work perfectly after following this guide :D. 

Regards,
Stew2

---

