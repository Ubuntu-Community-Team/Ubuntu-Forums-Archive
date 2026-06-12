---
title: "IDE DVD-ROM doesn't work after Suspend"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by wild_oscar on 2008-01-05
I have an odd behaviour on my Gutsy:

Whenever I resume from Suspend, my IDE DVD drive does not work. It cannot mount any cd or dvd, which works perfectly on my other, SATA dvd rom.

What could cause this behaviour?

---

### Post by kyphi on 2008-01-05
When I had a mixture of IDE and SATA DVD drives I had troubles too where the IDE drive would not be recognised in Ubuntu but was fine in XP.

The problem was solved by replacing the IDE drive with a SATA drive.

IDE and SATA drives work via separate controllers on your motherboard.

Why resuming from suspend should influence this I cannot tell.  You could try to set the slider for suspend in Power Management to 'never'.

---

