---
title: "Compiz color filters causing X to crash"
date: 2009-05-03
forum: Assistive Technology &amp; Accessibility
---

### Post by wch on 2009-05-03
I've been trying to use the Compiz color filters (enabled the Compiz Config Settings Manager), but whenever I enable the plug-in and then turn it on for a window or for the whole screen, X freezes up and then dies roughly 15 seconds later. During this time I'm able to move the mouse cursor, but nothing else happens on the screen. After the crash, I get the gdm login screen.

I can't seem to find any info about the crash in my Xorg.0.log, nor in my ~/.xsession-errors file. However, when I enable the filters (but before I actually turn them on and crash it), I get this in my .xsession-errors:

```

/usr/bin/compiz.real (colorfilter) - Info: Loading filter negative (item negative).
/usr/bin/compiz.real (colorfilter) - Info: Loading filter negative-green (item negative-green).
/usr/bin/compiz.real (colorfilter) - Info: Loading filter blueish-filter (item blueish-filter).
/usr/bin/compiz.real (colorfilter) - Info: Loading filter sepia (item sepia).
/usr/bin/compiz.real (colorfilter) - Info: Loading filter grayscale (item grayscale).
/usr/bin/compiz.real (colorfilter) - Info: Loading filter deuteranopia (item deuteranopia).
/usr/bin/compiz.real (colorfilter) - Info: Loading filter protonopia (item protonopia).
/usr/bin/compiz.real (colorfilter) - Warn: Tried to load 7 filter(s), 6 succeeded.

```

It says only 6 succeeded, but there are files for all 7 present in /usr/share/compiz/filters.

Other possibly useful info:
[LIST]
[*]The Negative plug-in works for a single window, but not for the whole screen. When I try to turn it on for the whole screen, there's no crash -- it's just that nothing happens. This is the standalone Negative plug-in, not negative filter file in the Color Filter plug-in.
[*]The machine is a Dell Mini 9 with Intel 945GM graphics, running Jaunty.
[/LIST]

Any ideas on what's happening here? My installation is pretty new and I haven't done much to it.

---

### Post by ShodoPan on 2009-07-09
I encountered this same problem.  As far as I can tell, this has something to do with having more than one filter enabled (like, present on the list of filters). It seems I can have any one filter on the list and it will work fine, but if I try to have two or more, it will crash X as soon as I try to turn a filter on. Hope this helps.

---

