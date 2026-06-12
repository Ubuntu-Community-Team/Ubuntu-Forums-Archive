---
title: "Brightness and Virtual Terminals - Gutsy"
date: 2008-01-21
forum: Apple PPC Users
---

### Post by stream303 on 2008-01-21
While working on restoring my lost virtual terminals in Gutsy on my G4 iBook, I also found that this solution also fixes the lack of brightness controls for the screen for this model.

Removing

**append="quiet splash video=ofonly"**

from /etc/yaboot.conf, reinitializing with sudo ybin -v, and then rebooting worked.  I don't mind the startup info being displayed instead of the distorted Ubuntu logo. :)

See this thread for more info:
[http://ubuntuforums.org/showthread.php?t=610767](http://ubuntuforums.org/showthread.php?t=610767)

For my G5 iMac, I'm still searching for brightness control, and about the only thing I can control is to take the edge off the bright screen a bit by altering the gamma slightly

```
xgamma -gamma 0.9
```

---

