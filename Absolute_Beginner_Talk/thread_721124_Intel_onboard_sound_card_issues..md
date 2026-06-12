---
title: "Intel onboard sound card issues."
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by balakumar on 2008-03-11
I used the posts in the forum to configure my onboard sound card but that does not seem to work.

I have a  82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller and i need to know where exactly i can get the alsa driver for it.Please help me out guys.

---

### Post by MaximusTG on 2008-03-11
Did a bit of googling, think you already have the right driver, it's a different kind of issue.

Try this:

Procedure:
- Open a command window
- Type
    alsamixer
- Use the right arrow to make the "highlighted selection" (
  red text under the "bar display" be the "Headphone Jack Sense"
  (these things are somewhat truncated under the bar displays, so
  that the "headphone" and "headphone jack sense" bars may read
  almost the same; however, the "Item" in the upper right corner
  of the command window spells it out.
- At the top of the bar may appear (or not) "MM"; typing an "m"
  toggles the "MM" on and off.  (Confusingly, "MM" equates to "off"
  and "not MM" equates to "on"; MAKE SURE THE MM APPEARS at the
  top of the "headphone jack sense" bar
- Do the same thing to "line jack sense", found by pressing
  the right arrow sufficient times; there are more bars than
  fit in a normal window so it might not appear initially;
  the additional bars scroll into the window as you move right
With the "MM" appearing at the top of both the "headphone jack
sense" and the "line jack sense" (meaning I presume that the
features are "off" or "disabled", my sound works.

Found on this site:
[https://www.redhat.com/archives/fedora-list/2005-January/msg05487.html](https://www.redhat.com/archives/fedora-list/2005-January/msg05487.html)

---

### Post by balakumar on 2008-03-11
alsamixer: function snd_ctl_open failed for default: No such device


this is what i get when i type alsamixer.

---

