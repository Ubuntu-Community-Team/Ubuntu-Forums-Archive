---
title: "[SOLVED] That SCIM thing"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Flyvapnet on 2007-07-24
Due to an error on my part, I recently had to reinstall Ubuntu 7.04 Feisty Fox; and mysteriously I'm now plagued with this unsightly SCIM thing which redundantly places two ugly icons (big bar-filling white backgrounds which look ridiculous when one wants transparency) at the top of the screen and occasionally produces a small dialog box in the lower-right corner of the screen (covering up Forecastfox).  How do I get rid of this visual pollution, which merely tells me what language I'm using -- something I'm well aware of already?

The more I read about SCIM, the less I understand why it's there and why it seems to resist being disabled.  If anyone can tell me, in user's terms rather than Geekspeak, how to turn this SCIM eyesore off I'd be very grateful.  Thank you!

:confused:

=^..^=

---

### Post by zanglang on 2007-07-24
Right-click the icon, select 'SCIM setup', go to 'GTK', change 'Show' to 'On Demand', and untick 'Show tray icon'. You'll have to do the same for your admin user with
> sudo scim-setup
For the second icon as well.

---

### Post by Flyvapnet on 2007-07-24
Thank you very much, **zanglang**, for your clear and timely advice!  I did what you suggested and it worked.  I'm very grateful for your help in this matter.

=D>

=^..^=

---

### Post by James Fitzpatrick on 2007-07-28
My problem is just the opposite.  I installed 7.04 on my laptop, but, although I have the icon on the top toolbar, I don't have the SCIM bar on the bottom and I can't seem to activate the SCIM for Hanguk at all.  I had to reinstall 7.04 on my desktop comp, and I have both the icon at the top, and the bar at the bottom, and it works fine.  The settings on both the laptop and desktop seem to be the same.  I must be missing something.  How do I activate the SCIM for Hangul on my laptop?

---

