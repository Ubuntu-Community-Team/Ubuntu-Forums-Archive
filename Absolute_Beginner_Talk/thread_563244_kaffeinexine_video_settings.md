---
title: "kaffeine/xine video settings"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by niteblind on 2007-09-29
Hi All,

Does anyone know how I can change the default video settings in Kaffeine. I have looked through the options and I cannot see anything there.

Every time I restart Kaffeine I have to increase the Contrast setting as it is set way under the half way mark and everything is too dark.

Any ideas?
niteblind

---

### Post by niteblind on 2007-10-02
noone know the answer to this then??

niteblind

---

### Post by mivo on 2007-10-02
Kaffeine's settings are saved in /home/<user>/.kde/share/config/kaffeinerc -- at the end of the text file you'll find this section:

[Video Settings]
Brigthness=-1
Contrast=-1
Hue=-1
Saturation=-1

Try making changes here while Kaffeine is not running.

---

