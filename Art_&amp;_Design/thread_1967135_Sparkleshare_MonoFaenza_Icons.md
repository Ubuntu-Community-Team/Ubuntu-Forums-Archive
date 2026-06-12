---
title: "Sparkleshare Mono/Faenza Icons"
date: 2012-04-27
forum: Art &amp; Design
---

### Post by clicker4721 on 2012-04-27
Hi everyone,

I just installed Sparkleshare to see what the big deal is. I like it, but, as is customary of anything that doesn't default Ubuntu-ish icons, the tray notification sort of sticks out. I found the files:
```
/usr/share/icons/hicolor/24x24/status/process-synicng-sparkleshare-i.png
/usr/share/icons/hicolor/24x24/status/process-synicng-sparkleshare-ii.png
/usr/share/icons/hicolor/24x24/status/process-synicng-sparkleshare-iii.png
/usr/share/icons/hicolor/24x24/status/process-synicng-sparkleshare-iiii.png
/usr/share/icons/hicolor/24x24/status/process-synicng-sparkleshare-iiiii.png

```

It would be much appreciated if somebody could make some mono icons for it that resemble the original, at least enough to identify it as Sparkleshare. I'm sure I'm not the only one that would benefit from them.

---

### Post by hbons on 2012-04-28
The icons have already been made and can be found here: [https://github.com/hbons/SparkleShare/tree/master/data/icons](https://github.com/hbons/SparkleShare/tree/master/data/icons)

The problem is that I need someone who knows about the build system and Ubuntu so they can be installed into the right places.

---

### Post by clicker4721 on 2012-04-28
> **hbons said:**
> The icons have already been made and can be found here: [https://github.com/hbons/SparkleShare/tree/master/data/icons](https://github.com/hbons/SparkleShare/tree/master/data/icons)

The problem is that I need someone who knows about the build system and Ubuntu so they can be installed into the right places.

Thanks! I'm just going to add ".old" to the ones currently set and put the new ones in their places. The weird part about where to put them is that their set position in /hicolor/ has the resolution then the purpose (/24x24/status/), whereas the light folders have purpose then resolution. I suppose you could add a 24x24 folder just within the icon set folder, but that hasn't yielded positive results for similar experiments by me in the past.

---

