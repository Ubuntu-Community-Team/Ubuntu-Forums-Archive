---
title: "Live CD display options"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by FogOgg on 2007-02-07
Just a simple question, admittedly I only spent a scant couple minutes trying to help myself on help.ubuntu but found it slightly overwhelming to search through.

I tried booting a live CD recently and was able to use a command line switch to load the first text menu fine, but when attempting to boot into Gnome the displays fails. It shows multiple screens overlayed as though the resolution or refresh is not supported by my monitor.

My monitor is rather old, being that it's the piece that came with my 386 some years ago and only supports a maximum of 800x600x32 at 60Hz. Is it possible to boot the live CD with these settings or is it possible my video card, a Matrox Millenium G400, or monitor just plain isn't supported, even by a generic driver?

---

### Post by Quintin Riis on 2007-02-07
Matrox cards are very well supported in Linux.

Your monitor is a piece of junk.  Suggest getting something newer.  You might want to try the alternate install disc, or maybe editing /etc/X11/xorg.conf and restarting X.

---

