---
title: "Lucid - MBP 5,2 doesn't suspend with lid close"
date: 2010-05-01
forum: Apple Hardware Users
---

### Post by thompsonj on 2010-05-01
When I close the lid on my Macbook Pro 5,2 running Ubuntu 10.04 nothing happens... it doesn't turn off the screen, suspend, hibernate or anything.  Everything that i've looked at says to change the setting in power management but there's no option there for what to do when the lid closes.  I've also checked out gconf-editor and the setting appear to be right in that... so I don't know what the issue could be.

Any help would be greatly appreciated.

---

### Post by kosumi68 on 2010-05-01
> **thompsonj said:**
> When I close the lid on my Macbook Pro 5,2 running Ubuntu 10.04 nothing happens... it doesn't turn off the screen, suspend, hibernate or anything.  Everything that i've looked at says to change the setting in power management but there's no option there for what to do when the lid closes.  I've also checked out gconf-editor and the setting appear to be right in that... so I don't know what the issue could be.

Any help would be greatly appreciated.

It may well be that your computer is not recognized as a laptop, at least not to the gnome power manager. In a terminal, you might want to try running
```

acpi_listen

```
the program may appear to produce no output, but if you close the lid and open it again, there should be a line or two of output. Knowing the lines are there would help rule out a set of possible reasons.

---

### Post by thompsonj on 2010-05-01
when I did that it says:

button/lid LID0 00000080 00000005
button/lid LID0 00000080 00000006


Is that what you were looking for?

---

### Post by kosumi68 on 2010-05-01
Yes, thanks. The reason there is a problem here might be related to a major migration that has been on its way since jaunty jackalope: moving control over from the system handler HAL to the more light-weight system handler udev. My guess is that the power manager asks one of the two the question "is this a laptop", and gets "no" as an (incorrect) answer. I am afraid it will take a few days for people to catch up on this problem, so don't hold your breath. I suspect it will manifest itself in several different forms before the root of the problem is found.

EDIT: as a quick-fix, if you want to suspend the machine:
```

sudo pm-suspend

```

---

### Post by benzolchemie on 2010-05-03
I think it's due to the power management issue on MBPs that some more guys are having at the moment - your laptop should suspend when running on AC power (if, of course, you have enabled the appropriate setting in the power management) but NOT while on battery (the corresponding tabs in the power management section are actually missing then).

All the best,

Dennis

---

### Post by thompsonj on 2010-05-03
Well... my problem is solved... but I have no idea why...? I just checked the power management settings again and the tabs that were missing just showed up!  So... no more issue... thanks guys

---

