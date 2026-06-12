---
title: "Macbook Pro 12,1 Suspend Issue Only On Battery"
date: 2023-09-03
forum: Apple Hardware Users
---

### Post by ptimme01 on 2023-09-03
Installed 22.04.2 on a Macbook Pro 12,1.  Everything works great (even the camera after an easy procedure).  The only issue is that suspend works when the AC is plugged in, but when it suspends while on battery the screen blanks and the only way to get it to come back is a hard reset.  Has newest Apple Firmware frfom Monterey install.  Would love just to have the same behavior as when it's plugged in.

---

### Post by MAFoElffen on 2023-09-04
I have a Macbook (3,1) that I picked up to make sure my scripts were compliant with Mac Hardware running Ubuntu. It is late 2007. I am running 22.04.3 on it. I believe yours is most likely early 2015 or newer.

Could you please run the [UbuntuForums 'system-info']("https://github.com/UbuntuForums/system-info") Script on it, and post the URL of where the report uploads to a pastebin?

Also, post within Code Tags:
```

gsettings list-recursively org.gnome.settings-daemon.plugins.power
gsettings get org.freedesktop.Tracker3.Miner.Files initial-sleep
grep . /sys/module/intel_idle/parameters/*
grep . /sys/devices/system/cpu/cpu0/cpuidle/state*/*

```

---

### Post by QIII on 2023-09-04
Moved to Apple Hardware Users.

---

### Post by MAFoElffen on 2023-09-06
Still following this, but no further info from the OP...

---

