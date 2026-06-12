---
title: "battery meter"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by timebomb on 2007-03-18
Still working through my transition to Ubuntu, and have made good progress.  My attention is now on the battery meter, which seems to be constantly charging and never seems to be full.  I have a Dell 600m with the BIOS updated to the most recent version.

The output for acpi is:
> Battery 1: charging, 69%, rate information unavailable.

Last week it was at 74%, and has fallen about a percentage every other day or so.  I have not unplugged the laptop in that time.  XP shows the battery fully charged.  I just do not think Ubuntu is reading the battery properly.

Advice appreciated.

---

### Post by kevincai96 on 2007-03-18
Well, you're correct. Ubuntu isn't always accurate, so just ignore it, or extend the battery life by sticking it in the freezer overnight. But since you said XP said its good, then it's really up to you now.
:lolflag:

---

### Post by McMarley on 2007-03-18
try

killall gnome-panel

in the terminal
might work

---

### Post by timebomb on 2007-03-18
Nope, that doesn't do it.

---

### Post by McMarley on 2007-03-18
you said i doesnt go above 66. does it go beneath?

---

### Post by timebomb on 2007-03-18
> you said i doesnt go above 66. does it go beneath?

That is not exactly what I said - sorry to be imprecise.  When I started observing the battery meter last week, it topped out at 74%, and has steadily drifted downward (now 68%).  I have not unplugged the laptop (until about 20 minutes ago).  It never registers as fully charged and is perpetually charging.

So yes - it goes down when I unplug the system.

---

### Post by timebomb on 2007-03-18
Not sure what I did, but it is working now and fully charged.  Hmmmm.

---

