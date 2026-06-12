---
title: "Firefox drop down menus not working"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by jvc26 on 2007-01-13
Hi there all, just a brief problem:

I installed a group of 3 add-ons to firefox: (see the .log file here:)
```

-------------------------------------------------------------------------------
http://releases.mozilla.org/pub/mozilla.org/extensions/noscript/noscript-1.1.4.5.061221-fx+fl+mz+zm.xpi  --  2007-01-13 16:12:53
-------------------------------------------------------------------------------


     Install completed successfully  --  2007-01-13 16:12:54

-------------------------------------------------------------------------------
http://releases.mozilla.org/pub/mozilla.org/extensions/adblock_plus/adblock_plus-0.7.2.4-fx+fl+zm+tb.xpi  --  2007-01-13 16:13:21
-------------------------------------------------------------------------------


     Install completed successfully  --  2007-01-13 16:13:21

-------------------------------------------------------------------------------
http://releases.mozilla.org/pub/mozilla.org/extensions/worldweather_/worldweather_-2.0-tb.xpi  --  2007-01-13 16:13:59
-------------------------------------------------------------------------------


     Install completed successfully  --  2007-01-13 16:14:02

-------------------------------------------------------------------------------
http://releases.mozilla.org/pub/mozilla.org/extensions/1-clickweather/1-clickweather-1.1.4-fx.xpi  --  2007-01-13 16:14:17
-------------------------------------------------------------------------------


     Install completed successfully  --  2007-01-13 16:14:17

```

However on then restarting firefox it became unresponsive and refused to do anything - the only way to stop it was via force quit. Consequently I removed the plugins from the extensions folder and now it loads and runs with no problems whatsoever. However, now on sites such as the forums, where there were once drop down menus (such as search, quick links etc, there is now no menu, just that top function (i.e. search and quick links loads me straight into post new reply) Not only that but I can no longer use the buttons on the new reply which allowed me to put the code tags and quote tags in quickly.

How can I remedy this awful situation?
Thanks for your replies,
Il

---

### Post by riven0 on 2007-01-14
I bet it's something related to that noscript file. Have you tried manually trying to locate it? Perhaps it installed one of the configuration files elsewhere:

> updatedb

> locate noscript

Otherwise, maybe a reinstallation of firefox is in order...

---

### Post by jvc26 on 2007-01-15
Hi there it ended up having with a reinstall, but even after a full --purge remove, and going through finding every possible firefox file and removing it it didnt stop the problem- it ended up faster to just reinstall the base ubuntu system and now it all works fine (I have reinstallation down to a fine art now ;)) I wish I'd known an easier way to do it, but so every one has a heads up on this - installing those three add-ons together causes firefox to crash incessantly (I tried it a couple more times just to make sure it wasnt a one off) even if I installed all of them separately then they would break when they all launched together... weird - it may be to a conflict between the noscript one and the weather one... who knows? Anyway just as a warning for those who might be interested that seems to be the case.
Il

---

### Post by tommcd on 2007-01-15
In the future you could probably just delete your FF profile or create a new profile. See this:
[http://www.mozilla.org/support/firefox/profile#new](http://www.mozilla.org/support/firefox/profile#new)
On my system it only works like this:
 firefox -ProfileManager (I have to leave off the < ./ >).
Be sure to close FF first. You can then create a new profile and or delete the old one.
Also, see this for another way:
[http://ubuntuforums.org/showthread.php?t=103930&highlight=firefox+profile](http://ubuntuforums.org/showthread.php?t=103930&highlight=firefox+profile)
Reinstalling FF does not create a new profile. This is how you can keep your bookmarks and settings when upgrading FF.

---

