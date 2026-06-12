---
title: "No sound, can't unmute sound card"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by toucans on 2007-12-09
Hi,

I can't get any sound at all from my computer. I'm using Xubuntu on a laptop, and it appears to recognize my sound card (HDA Nvidia). The mute button on the laptop always stays orange (off), even though PCM in alsa mixer says it's at max volume. I've tried the various guides I found online, but they haven't worked.

Any ideas?

---

### Post by Orivel on 2007-12-10
You can try using OSS v4. It's an alternative to ALSA. A guide to install it can be found [here]("http://ubuntuforums.org/showpost.php...4&postcount=60")

---

### Post by rockinlinux on 2007-12-10
oss might work, its wortha shot. It could also be that there is a bug. please post your lspci output, or tell your exact sound card please.

---

