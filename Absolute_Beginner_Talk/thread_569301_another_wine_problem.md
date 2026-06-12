---
title: "another wine problem"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by irishgoth8822 on 2007-10-06
for some reason, almost every exe i try to run with wine gives me this code:

```
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.


```

what have i done/forgot to do?

---

### Post by Clay_Banger on 2007-10-07
it appears to be a problem with the sound settings. type "winecfg" into the terminal and select the sound tab. have a play around there with the settings to see if anything will let it work, but my guess is to untick alsa or configure the place that the sound card is.

---

### Post by Frak on 2007-10-08
type winecfg in the terminal, navigate to audio, and load the ALSA driver.

---

