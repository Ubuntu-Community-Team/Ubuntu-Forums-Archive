---
title: "Help!  I need sound drivers for DFI on-board sound."
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by old_geekster on 2007-01-16
This afternoon, I updated the video drivers (nVidia-glx) for my card.  Now, I don't have any sound.  Does this make sense?:confused: 

How do I find and install sound drivers for the on-board (karajan) on my board?  Please see my sig.

I will appreciate your any help!

Update:  I found "AlsaMixer v1.0.11" on my system.  It says that my card is a nVidia CK804; Chip: Realtek ALC850  rev 0, but I still can't figure out why I don't have sound.  It worked fine all day.

---

### Post by crispy_420 on 2007-01-16
I don't see how video drivers messed up sound but if they did, they did.

Start from the beginning:

1. Check that they are on. You can check easily from the panel's volume control by right clicking      -> Open Volume Control

2. Check sound preferences: System -> Preferences -> Sound

3. running lspci reports the card?

Just a starting point, gotta get ready for work, check back in a few hours.

---

### Post by old_geekster on 2007-01-16
Thanks, crispy!

I am not saying the the video drivers actually caused the problem.  What I am saying is "the only change that I made to the system was video drivers".

When I ran the command that you provided, it gave me all of the info on my video card, but didn't show my on-board sound module.

I guess I will delete the sound drivers and reinstall them to see if that helps.

I had already check all of the other items that you suggested.

---

### Post by s1l3ntdeth on 2008-01-20
I'd be interested as I am having the same issue. I just did a fresh load, and updated my nvida display driver with the same results.

:confused:

---

