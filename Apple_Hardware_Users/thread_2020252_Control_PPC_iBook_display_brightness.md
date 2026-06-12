---
title: "Control PPC iBook display brightness?"
date: 2012-07-07
forum: Apple Hardware Users
---

### Post by Ranko Kohime on 2012-07-07
I recently recommissioned an iBook G4 for use as a file server, however I can't seem to control the display brightness in 12.04.

I'd like to have the backlight off fulltime, even when I'm controlling the iBook through VNC.  The following command, issued via SSH, will shut the display off, but as per it's design, won't keep it off:

```
xset -display :0 dpms force off
```

The fn-modified function keys only partially work, giving me the ability to control the volume, but not the screen brightness.

---

