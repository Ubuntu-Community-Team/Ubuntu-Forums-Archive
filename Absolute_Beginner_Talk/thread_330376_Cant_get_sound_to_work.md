---
title: "Cant get sound to work"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by gabz on 2007-01-03
On integrated ASUS A7N8X. What can I do? Please help me.

---

### Post by pseudonym on 2007-01-03
You can check out the [Comprehensive Sound Guide]("http://www.ubuntuforums.org/showthread.php?t=205449") if you haven't already.

ALSA should work perfectly with your board, using the snd-intel8x0 driver. I know this because I used to own the deluxe model A7N8X.

If you're feeling adventurous you could also try using the nvidia nforce sound driver. It's most useful if you have an nforce2 motherboard with 'SoundStorm' Dolby Digital audio, but I found the quality even on the normal AC97 audio to be better than ALSA. There is a great [howto]("http://www.ubuntuforums.org/showthread.php?t=253725") on these forums, but it involves some extra work to set it up.

HTH :)

---

