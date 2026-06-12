---
title: "Ugh I killed Firefox"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by PhillyB on 2007-03-20
Somehow I cant manage to start firefox.  If I go system-administration-synaptic program manager- then choose firefox, and reinstall I can get back in again.  As soon as I close firefox I get the following message.  Which I am about to create and come back here and post once I kill firefox.

alert

Error launching browser window:  no XBL binding for browser

Comes up in a popup when I click on firefox.

---

### Post by CSandman on 2007-03-20
In synaptic try removing it completely, do a system reboot by typing 

sudo shutdown -r now 

into a console then back in synaptic try installing it again.  It may just be a minor hiccup.

---

### Post by mozkaynak on 2007-03-20
you can also try the following link:

[http://www.mozilla.com/en-US/firefox/releases/fix-extensions.html](http://www.mozilla.com/en-US/firefox/releases/fix-extensions.html)

---

### Post by antmenj on 2007-09-13
> **mozkaynak said:**
> you can also try the following link:

[http://www.mozilla.com/en-US/firefox/releases/fix-extensions.html](http://www.mozilla.com/en-US/firefox/releases/fix-extensions.html)

I had this "*XBL*" problem too.  It happened after trying some extensions that worked when installed but not after a reboot.

The above wouldn't work as I wasn't able to rename or replace the chrome folder with the GUI or in the terminal as it seems to be locked some how.

In the terminal ```
firefox --safe-mode
``` got me in and allowed me to uninstall extensions via tools menu :) few .

---

