---
title: "How can i remove modules from autoload?"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by v3rtigo on 2006-12-06
When i first installed ubuntu edgy it detected my hardware and autoloaded many modules

the problem is that i have onboard card and sblive5.1
I want to remove completely the onboard card support

but can't find where i can remove the modules from autoload...

there is many sound modules in lsmod that i don't need 
/etc/modules contains nothing.

---

### Post by po0f on 2006-12-06
v3rtigo,

The easiest solution would be to just disable the onboard sound through the BIOS.  If, for whatever reason, you can't do this, you can blacklist the module that gets loaded for the soundcard in /etc/modprobe.d/blacklist.

---

