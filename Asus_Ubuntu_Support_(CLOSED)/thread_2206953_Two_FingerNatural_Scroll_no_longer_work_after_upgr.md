---
title: "Two Finger/Natural Scroll no longer work after upgrading to 13.10"
date: 2014-02-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by oneseventeen2 on 2014-02-21
Ever since upgrading to 13.10 my synaptics trackpad no longer seems to support two finger scrolling or natural scrolling. Edge scrolling works, but tap to click, and tap & drag do not work either.

When I view the mouse & touchpad settings I see checks next to both two finger scroll and natural scrolling.  Disabling and re-enabling these does not change anything.

You can see my synclient here: [http://paste.ubuntu.com/6971811/](http://paste.ubuntu.com/6971811/) 

I'm sure this is something simple that I'm overlooking, or perhaps it is because I borked with something years ago to get two finger scrolling working, who knows?

This is on an ASUS U31SD laptop with a Synaptics touchpad.

Any thoughts?

---

### Post by oneseventeen2 on 2014-02-22
It was, as I expected, user error!

I had installed cinnamon as my desktop environment and apparently the settings manager isn't actually changing my settings.

I made the changes by running dconf-editor and browsing to: /org/cinnamon/settings-daemon/plugins/mouse/ to make my changes there.

Now I can use two fingers for horizontal and vertical scrolling, natural scrolling, and tap to click!  WooHoo!

---

