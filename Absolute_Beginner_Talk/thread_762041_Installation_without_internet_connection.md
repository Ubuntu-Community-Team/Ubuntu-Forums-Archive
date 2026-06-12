---
title: "Installation without internet connection"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by frogzombie on 2008-04-21
After installing Ubuntu 7.10 without an intitial internet connection, I cannot now install updates or apt-get update.

For apt-get, it gives me 2 updates over and over again, 2 translation packages. As for my update manager, it says that it's up to date, tries downloading 6 files that aren't showing up in the update list, then says it's up to date.

Any suggestions?

---

### Post by stchman on 2008-04-21
> **frogzombie said:**
> After installing Ubuntu 7.10 without an intitial internet connection, I cannot now install updates or apt-get update.

For apt-get, it gives me 2 updates over and over again, 2 translation packages. As for my update manager, it says that it's up to date, tries downloading 6 files that aren't showing up in the update list, then says it's up to date.

Any suggestions?

Next time it tells you to update, uncheck the boxes next to the updates.  This will tell Ubuntu that you do not want to install these updates at all.

---

### Post by frogzombie on 2008-04-21
Well, for the update manager, There is nothing in the list. When I check for updates, it downloads 6 files, and then there is still nothing in the update list.

---

### Post by mikeyphi on 2008-04-21
> **frogzombie said:**
> After installing Ubuntu 7.10 without an intitial internet connection, I cannot now install updates or apt-get update.

For apt-get, it gives me 2 updates over and over again, 2 translation packages. As for my update manager, it says that it's up to date, tries downloading 6 files that aren't showing up in the update list, then says it's up to date.

Any suggestions?

Hi there and welcome!

Open Systems/Administration/Software Sources
enable the first 4 choices. De-select the CD-ROM choice (if present)

---

### Post by frogzombie on 2008-04-21
Thank You, That took care of it. I had to open up the 3rd party driver option as well, but it worked like a charm. Thanks!

---

