---
title: "Old Sound Blaster Problem."
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Teh Dust on 2007-05-11
After upgrading to vista and hating it, I recommended that my friend switch to Ubuntu. He tried it out on my PC and loved it so we installed it on his older pc.

We ran into 2 problems. First the wireless which was a broadcom chip and easy to fix.

But the sound card is giving us trouble.
It is a Creative Sound Blaster. The model number on the card is CT4740 and in the hardware information it shows up as a Ensoniq 5880. I tried upgrading ALSA, and adding acpi=ht to he grub boot, but still nothing is working.

Help would be greatly appreciated. Please don't let me reinstall windows!

---

### Post by happyhamster on 2007-05-12
This is a good place to start:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

(You'll have to use the snd-ens1371 driver)

---

