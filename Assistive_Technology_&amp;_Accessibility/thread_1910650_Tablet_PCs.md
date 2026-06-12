---
title: "Tablet PCs"
date: 2012-01-17
forum: Assistive Technology &amp; Accessibility
---

### Post by HalfAnAndroid on 2012-01-17
I have a Toshiba tablet PC, and can't find a screen rotation utility that doesn't invert the mouse for the stylus. When I rotate the screen, I drag the stylus up, and the mouse goes down. If I have it in portrait mode, if I drag it left, it goes up, etc. Does anyone know of a screen rotation package that could solve my problem?


Thanks,

HalfAnAndroid

---

### Post by Favux on 2012-01-17
Hi HalfAnAndroid,

Welcome to Ubuntuforums!

I'm going to guess you are using either Natty or Oneiric.  That is because both of them have a default version of xf86-input-wacom that has a bug.  The Portrait orientations are reversed, i.e. cw and ccw are swapped.

The fix is either to make the swap in your rotation script or to update the xf86-input-wacom package.  See either the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") or the [LinuxWacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").

---

