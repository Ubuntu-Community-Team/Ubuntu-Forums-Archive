---
title: "Azureus problems on Gutsy"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by PogMoThoin on 2007-10-29
I'm having problems with azereus, it closes straight away after i open it. I've checked my java version. This is waht i get
> java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)


Is there any other java plugin i should have installed. What do i do? Have the latest version of azureus dl'in just in case. Which version of java do i need?

---

### Post by powder on 2007-10-29
Try renaming the .azureus folder in your home directory to .azureus_backup and then run Azureus again.

---

### Post by taurus on 2007-10-29
Run it from a terminal so you can see the exact error message for it.

```
azureus
```

---

### Post by PogMoThoin on 2007-10-29
Ran it from terminal, this is what i get:
> changeLocale: *Default Language* != English (Ireland). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Ireland)' (en_IE), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E4350500214), pid=8060, tid=3084913552
#
# Java VM: Java HotSpot(TM) Server VM (1.6.0_03-b05 mixed mode)
# An error report file with more information is saved as hs_err_pid8060.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)


---

### Post by prshah on 2007-10-29
Try deleting your logs from the ".azureus" folder in your home dir. You may have to setup a small script to do this everytime.

Cheers,
Priyasen

---

### Post by PogMoThoin on 2007-10-29
Deleted error logs & still get same thing.

---

### Post by PogMoThoin on 2007-10-29
> **powder said:**
> Try renaming the .azureus folder in your home directory to .azureus_backup and then run Azureus again.

This worked, cheers m8 :guitar:

---

