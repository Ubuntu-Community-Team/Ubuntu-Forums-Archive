---
title: "latest 6.06lts update breaks openoffice"
date: 2007-10-13
forum: Apple PPC Users
---

### Post by vector on 2007-10-13
Yesteday my ubuntu indicated there was an update.6.06lts. powerbook G3 pismo
clicking on the icon there was indeed a massive upadate. 130 odd files from memory. 200odd meg. I vaguely recall openoffice being apart of the upgrade.
So far most things seem to be ok but Open office refuses to open anything.Gives me an unexpected crash error, will recover files (but there arnt any) and relaunch 
this loop continues.

any thoughts?

ooffice -writer
/usr/lib/openoffice/program/soffice: line 222:  8535 Bus error               "${ sd_prog}"/pagein -L"${sd_prog}" ${sd_pagein_args}

when run from a terminal

---

### Post by vector on 2007-10-20
finally fixed. Alot of messing about removing ooo from the machine. Took a number of purge's and such.Dependancy problems and broken things didnt help but eventually the machine was cleared. I re installed writer (only) and even then on its first launch it collapsed into recovery mode but this time it allowed me to try and recover rather than re-launch and after two or three recovers finally the writer screen came up.

It seems something badly broke and lingerd within the system disabling recovery before hand.

---

