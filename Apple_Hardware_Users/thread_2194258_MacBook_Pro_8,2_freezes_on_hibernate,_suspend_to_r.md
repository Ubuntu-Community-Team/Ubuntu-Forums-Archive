---
title: "MacBook Pro 8,2 freezes on hibernate, suspend to ram works fine"
date: 2013-12-17
forum: Apple Hardware Users
---

### Post by andrew53 on 2013-12-17
I installed Ubuntu 11.10 (kernel 3.11.0-14-generic) on my MacBook Pro 8,2 (early 2011). Everything seems to work Ok, except for hibernation (suspend to RAM works flawlessly too).
I followed PM debugging instructions here: [https://www.kernel.org/doc/Documentation/power/basic-pm-debugging.txt]("https://www.kernel.org/doc/Documentation/power/basic-pm-debugging.txt") and it can't pass "platform" test. Like this:

```
# echo platform > /sys/power/pm_test
# echo platform > /sys/power/disk
# echo disk > /sys/power/state
```
At this point, the screen goes blank, then if freezes without turning off

Again, suspend to ram works flawlessly, so I don't think there is a problem with drivers.
I am using a swap partition (8GB RAM, 8GB swap), but the "platform" test failure indicates that the problem happens earlier (ACPI?).
I've also tried to do 
```
# echo shutdown > /sys/power/disk
# echo disk > /sys/power/state
```
with the same result (hangs instead of turning off).

Does anyone have any tips where to go from here?

---

