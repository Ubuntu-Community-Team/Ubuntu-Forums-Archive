---
title: "alsaconf missing"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by basfrank on 2006-10-10
Hi,

i want to configure my old sb 16 isa card via alsaconf and i have alsa-base and alsa-utils installed. but the bash says command unknown.

Whats the problem?
Please help me.

Bastian

---

### Post by jeelliso on 2006-10-10
Neither alsa-base nor alsa-utils installs alsaconf as it was removed for the Breezy release (I believe) because it is not needed.  If you really need alsaconf, take a look at [http://ubuntuforums.org/showthread.php?t=156975&highlight=alsaconf]("http://ubuntuforums.org/showthread.php?t=156975&highlight=alsaconf").

You may also run the man on alsactl or alsamixer.

~Justin

---

