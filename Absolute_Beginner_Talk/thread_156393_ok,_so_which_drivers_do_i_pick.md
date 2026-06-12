---
title: "ok, so which drivers do i pick?"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by vatechtigger on 2006-04-06
I want to install ubuntu for the first time. Ive been looking around for drivers for my hardware before I start. I have an Abit AV8 motherboard which uses the VIA KT800pro chipset. On the via page for linux drivers ot lists

Linux XFree86 (Not distribution-specific)
Fedora Core 3.0 Linux
Fedora Core 1.0, 2.0 & 4.0 Linux
Mandrake / Mandriva Linux
Red Flag Linux
Red Hat Linux
SuSE Linux

which one of these is compatible with Ubuntu, if any. Thanks for the help in advance

---

### Post by taurus on 2006-04-06
I don't think you need any driver for your mobo.  If you want to check to make sure Ubuntu runs fine on your machine, try booting off the LiveCD and if the LiveCD works, then the install version should work as well.

---

### Post by vatechtigger on 2006-04-06
Yeah, I guess I will just give it a try. For future reference though what are the similarities between the distros? For example, is unbuntu and red hat or suse, debian etc all based on the same core and are drivers for one compatible with one another?

Thanks for the quick reply!

---

### Post by taurus on 2006-04-06
Ubuntu is based on Debian but you still can install apps in RPM (RedHat/Fedora Core) format with alien...
```

sudo alien filename.rpm <-- conerting RPM to deb format
sudo dpkg -i filename.deb <-- install the deb version of the file

```

---

