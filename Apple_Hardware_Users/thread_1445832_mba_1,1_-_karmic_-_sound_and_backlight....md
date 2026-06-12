---
title: "mba 1,1 - karmic - sound and backlight..."
date: 2010-04-03
forum: Apple Hardware Users
---

### Post by pavel protin on 2010-04-03
hi.

i just installed karmic as sole OS on my macbook air.  i followed [these]("https://help.ubuntu.com/community/MacBookAir1-1/Karmic") instructions. except, i am a complete noob, so i can't make heads or tails of command lines. 

when it came to sound, i was able to (a) write the missing line into etc/modprobe.d/alsa-base.conf and (b) run depmod and reboot. but: part (c) of the instruction - "update the ramdisk" - was quite another story. in the documentation, it says i should use...

sudo update-initramfs -u -v -k `uname -r`

...but since i didn't know what to write instead of 'uname -r', i just left it out and ran the thing (seeing that the list of functions for that command said that this would update 'all' - of whatever). so. 

sound still doesn't work. what did i do wrong?

thanx in advance!

---

### Post by pavel protin on 2010-04-03
done. the problem seems to have been was a typo in modprobe. 3rd time's the charm.

---

