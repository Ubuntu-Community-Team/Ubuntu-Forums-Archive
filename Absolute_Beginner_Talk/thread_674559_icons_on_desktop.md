---
title: "icons on desktop"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-21
i noticed that every time i open a location in under the Computer location (external hard drive for example) a shortcut to the device is automatically placed on the desktop- then upon reboot the shortcut disappears. how can i disable shortcuts from appearing on the desktop every time i open a new location?  thanks.

---

### Post by PeterJS on 2008-01-21
What you're seeing is not a (direct) causal relation. The icons are showing up on the desktop because the devices are being mounted. Mounting a partition is a required prerequisite to browsing it. The settings for what shows up on the desktop can be found in GConf Editor in apps > nautilus > desktop.

---

