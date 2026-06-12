---
title: "Sound issue on hp pavilion"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by harry rao on 2008-03-14
the sound isn't working from the initial boot and i've tried the alsamixer and all volume settings are at max. 

is there anything that i can do to get sound working?

---

### Post by spiderbatdad on 2008-03-14
This wiki offers several workarounds.[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
Before getting too deep, you could try a simple attempt at setting default sound card. Run command:```
asoundconf list
asoundconf set-default-card Parameter
``` where Parameter is  the output derived from the fist command. Then reboot system. If no love, proceed to wiki linked above.

---

### Post by harry rao on 2008-03-14
alright i'll give that a go,
and my notebook is on the affected list - it's in the hp dv9000 series.

---

### Post by harry rao on 2008-03-14
everything worked just fine,
the sound is working after i followed the instructions off the link you gave me.

thank you.

---

