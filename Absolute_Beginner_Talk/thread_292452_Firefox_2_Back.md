---
title: "Firefox 2 Back"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-11-03
When I had the old Ubuntu version. On Firefox, when I hit the backspace, I could go back. But I can't do that with Firefox 2. Please help. Thanks!

---

### Post by whatintheworldisthat on 2006-11-03
Never noticed this before, backspace isn't working for me either. Not a problem though because I use my back/forward buttons on my mouse. (mx518)

---

### Post by ishift on 2006-11-03
how about this:

[http://www.pthree.org/2006/11/01/firefox-2-backspace/](http://www.pthree.org/2006/11/01/firefox-2-backspace/)

:)

---

### Post by towsonu2003 on 2006-11-03
set browser.backspace_action to 0 in about:config (type "about:config" in your browser, search for "backspace", and change the integer there).

more info here: [http://kb.mozillazine.org/Browser.backspace_action](http://kb.mozillazine.org/Browser.backspace_action)

Backspace was removed bc 
1. it was causing data loss
2. Linux doesn't use backspace to go back in history

See: [https://launchpad.net/distros/ubuntu/+source/firefox/+bug/60995](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/60995) for firefox distributed in ubuntu

and [https://bugzilla.mozilla.org/show_bug.cgi?id=351218](https://bugzilla.mozilla.org/show_bug.cgi?id=351218) for Firefox upstream (upstream = Firefox as it is distributed by mozilla.org)

---

