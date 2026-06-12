---
title: "Suspend help! - PowerbookG4, Gutsy"
date: 2007-11-16
forum: Apple PPC Users
---

### Post by dougiep on 2007-11-16
Hi,


Recently returned to ubuntu after a year, and have installed Gutsy (desktop) on an old G4 Powerbook (1.6ghz, 512mb ram, mobility radeon 9600 rv350 m10); it is running compiz.

Unfortunately I haven't been able to get suspend or hibernate working: gconf-editor seems to think 'can_suspend' is ok, hardware information shows that 'power_manager.can_suspend', but there is no 'Suspend' option on the quit menu (System>Quit), power management doesn't have any suspend options, and 'pbbuttonsd' returns : 'WARNING: No event devices available. Please check your configuration.' (then sits there blinking at me)

I've searched on google and here, but no one seems to have the exact issue or solution.

Any help would be great :-)

---

### Post by sulobanks on 2007-11-17
It's a known bug
[https://bugs.launchpad.net/ubuntu/+bug/144305](https://bugs.launchpad.net/ubuntu/+bug/144305)

I haven't actually figured out how to apply the patch yet (so if you do, let me know), but I have figured out how to hit ctrl-alt-F1 (switch to virtual terminal 1) and then sudo /usr/lib/hal/hal-system-power-pmu sleep.

I created a file called sleep with that line in it and set it executable so that I can just type ./sleep

It's not incredibly convenient, but it beats shutting down every time I need to go afk for a bit.

---

