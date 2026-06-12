---
title: "Lubuntu Live CD on USB Boots to Busy Box"
date: 2013-05-05
forum: Apple Hardware Users
---

### Post by heat33330 on 2013-05-05
Hi, I have a Powerbook G4 15" 1.67GHz last revision and I want to install Lubuntu on it. I placed the files from the ISO onto my flash-drive using disk image. When I boot from USB everything goes fine until the loading screen with Lubuntu and the dot-things. After the loading screen it boots into Busy Box. I've tested it with 12.04 and 13.04 and it's always the same result. Could someone please help me?

---

### Post by canhoto on 2013-05-06
Hi.

See if [this]("http://ubuntuforums.org/showthread.php?t=2141774") thread helps. Especially the answers from michiganmac.

---

### Post by heat33330 on 2013-05-12
I tried the radeon boot parameters but it still boots into BusyBox. Does anyone else have any ideas?

---

### Post by str8bs on 2013-05-12
Based on what others have reported on similar but not identical hardware, I might try ruling out several possible issues by:
```
live snd-powermac.blacklist=yes video=offb:off video=radeonfb:off radeon.agpmode=-1
``` or maybe even add b43.blacklist=yes to that long list.

If not, you may want to try the alternate installer. It may let you complete an install, but will have the same issues after completion. We might be able to get some logs to see what the problem is though.

Good luck.
Str8

---

