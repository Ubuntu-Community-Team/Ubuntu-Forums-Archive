---
title: "slow graphics with dual video cards, 4 monitors"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by port23user on 2007-12-20
I've got Gutsy installed and it works great, except for my graphics.  I'm contemplating going back to XP if I can't figure it out.  The problem comes because I'm running four monitors off two nvidia video cards.  Here's what I've tried:

1. Used TwinView on both cards.  This worked pretty well performance-wise (running proprietary nvidia drivers).  However, I'm guessing the screens were segmented off by video card--so if I had a window, I couldn't drag it to all four monitors--just the other monitor attached to the same video card.

2. This is what I'm using now.  I have it set up to use separate x screens for all monitors.  I have Xinerama enabled.  I can drag screens all the way across four monitors.  However, this is a huge performance problem for me (at least the way I have it configured, maybe).  It takes a while (~1-3 seconds) to load up a window.  It's slow to resize windows and minimize and restore and scroll.  Pretty much everything has a lag now.  I don't think it should be like this because 1) my hardware is all pretty current and 2) it wasn't this slow when I was running TwinView.

So my question is: what can I do???  It seems like I've tried everything and I've been working at this for weeks.  I'd go back to TwinView if I could drag windows across all the screens.  I'd stick with my current setup if it were faster.  Otherwise I might have to do XP so I can actually get my work done =(

---

### Post by Dyus36 on 2008-01-03
im having a similar problem as well, i have 3 monitors, 2 17in on a nvigia 6800gs and a 19in wide on a new 8500gt, right now im on the separate x w/ xinerama. like port says, its slow when dragging windows between the 2 cards, compiz and awn no longer work, but only when xinerama is enabled, and twinview only works between the 2 screens on the same card. anyone have any ideas/suggestions?

---

### Post by Ratham on 2008-01-04
Hi- I'm having problems getting two video cards (one onboard, one a PCI NVIDEA) to work at all.  Dyus36, would you mind posting your XORG.CONF file?  Then I can report back on what performance lags, if any, that I get.  Thanks!

---

### Post by Ratham on 2008-01-08
FYI, I gave up on my old configuration and just bought a new mobo with a PCI Express x16 slot and a new Nvidia card.  Dual monitors are working beautifully with TwinView for me now!

---

