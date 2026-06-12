---
title: "iBook keyboard caps lock as control [solved]"
date: 2009-05-04
forum: Apple Hardware Users
---

### Post by ramenite on 2009-05-04
Another item from the "stuff I had to find out about Linux on an iBook and thought it may be useful to someone else".

If you have an iBook, and want to swap the caps lock and control keys, before you swap them, you have to do this(with privs):

echo 1 > /sys/module/adbhid/parameters/restore_capslock_events

This will let the caps lock events be reported normally, so you actually make use of the caps as a control.

---

### Post by otakuj462 on 2011-02-11
Thanks for this, I was stumped. 

There's a bug in Launchpad on this issue that's been open since 2007: [http://art.ubuntuforums.org/showthread.php?t=1149092](http://art.ubuntuforums.org/showthread.php?t=1149092)

---

