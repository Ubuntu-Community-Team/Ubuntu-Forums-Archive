---
title: "Is there a clock that displays seconds?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by tc101 on 2007-06-22
Is there a clock that displays seconds?  I want to see the seconds click past for timing things.

---

### Post by Swab on 2007-06-22
Right click on the clock > preferences > show seconds

---

### Post by oilchangeguy on 2007-06-22
> **tc101 said:**
> Is there a clock that displays seconds?  I want to see the seconds click past for timing things.

right click the clock, and choose preferences. the place a check in the box for show seconds.

---

### Post by NeoLithium on 2007-06-22
If you right click on the clock on the panel, and select preferences, you can check the box which says "Show Seconds"

---

### Post by tgalati4 on 2007-06-22
I've seen linux-based stopwatches.  Try a search in synaptic.

---

### Post by yabbadabbadont on 2007-06-22
```
xclock -d -strftime '%T' -update 1
```
:D

---

### Post by floke on 2007-06-22
Cairo-clock

---

### Post by tc101 on 2007-06-22
Thanks everyone.  I've got it.

---

### Post by ryanVickers on 2007-06-22
Is there some way to change how it shows the data?  Right know, it's "Fri 22 Jun, 4:48:22 PM"  I would prefer something like "Fri, Jun 22, 4:48:22 PM"

I know KDE has some way of changeing that, and tons of other related things, like how to show numbers, currency, etc. ,but what about in GNOME?

---

### Post by Fornax-101 on 2007-06-22
Well, jou should start gconf-editor.
Then goto: apps => panel => applets => applet_0 (Where bonobo_iid says Clock ) => prefs
and put in custom_format: "%a, %b %d, %H:%m:%S" & format: "custum".

That should do it:)

For other formating options see the man page of strftime.

---

