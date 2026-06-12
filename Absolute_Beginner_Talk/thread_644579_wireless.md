---
title: "wireless"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by mithridatism on 2007-12-19
hey,

im a first time poster. i know theres a wireless thread, but im a newbie and mostly wander around aimlessly til' i cobble together some idea of what to do.

im running a HP dv9000t series laptop with Intel PRO/Wireless 4965AGN Network Connection and Bluetooth. i found a site that had the driver for 4965AGN (didnt say anything about bluetooth...but i just want wifi to work...so i didnt think it mattered). 

but before installing the driver, i needed to install this (at least from what i understood):
[http://intellinuxwireless.org/?p=mac80211&n=howto-mac80211](http://intellinuxwireless.org/?p=mac80211&n=howto-mac80211)

i got to the line where it told me to "make" and i ran in to trouble

----------

yoshi@shadymilkman:~$ cd mac80211-10.0.2
yoshi@shadymilkman:~/mac80211-10.0.2$ make

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

Kernel Makefile not found at '/lib/modules/2.6.22-14-generic/source/'
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Error 1

yoshi@shadymilkman:~/mac80211-10.0.2$ make SHELL=/bin/bash
Kernel Makefile not found at '/lib/modules/2.6.22-14-generic/source/'
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Error 1

yoshi@shadymilkman:~/mac80211-10.0.2$ 

--------------

whats all this stuff? :confused:

many-a-thanks


ps:
the original driver site is here:
[http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi)
im doing this right...right?...?

---

### Post by shadow-of-sin on 2007-12-19
You may want to try this guide instead:
[http://ubuntuforums.org/showthread.php?t=471794](http://ubuntuforums.org/showthread.php?t=471794)
(its written specifically for Intel PRO/Wireless 4965)

---

