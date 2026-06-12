---
title: "lspci"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by FoggyMtn on 2006-08-16
HEy Ya'll

I want to play around with some different distros.  I need a list of how all of my current hardware is configured.  Is lspci the best tool to generate this list?  Or will that leave out some vital specs I'll need down the road to reinstall ubuntu?

Thanks
rob

---

### Post by kebes on 2006-08-16
You should run a bunch of commands and save the output of all of them:

```

lspci
scanpci
/usr/X11R6/bin/Xorg -scanpci
cat /proc/cpuinfo

```

There will obviously be some overlap between the output of those commands, but it's better to have more information than not enough!

---

### Post by FoggyMtn on 2006-08-16
Thank you!  That's what I needed to know!!

rob

---

