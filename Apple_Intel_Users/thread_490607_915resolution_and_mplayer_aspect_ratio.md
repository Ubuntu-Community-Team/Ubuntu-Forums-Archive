---
title: "915resolution and mplayer aspect ratio"
date: 2007-07-02
forum: Apple Intel Users
---

### Post by grim1234 on 2007-07-02
Any video played by mplayer on my macbook has an incorrect resolution. The video is 4:3 but is now closer to 16:9 with black bars on the edges when fullscreen. this is with the cli mplayer.

It's probably to do with the 915resolution hack to get the correct aspect ratio working.

Does anyone know a solution?

---

### Post by grim1234 on 2007-07-04
Just in case anyone else has the same problem, I've fixed it now. You need to edit /etc/mplayer/mplayer.conf and add the line "monitoraspect = 1.6" for a 1280x800 resolution.

If you have a different resolution just change the value (it's x/y, ie 1280 / 800 = 1.6)

---

### Post by ronocdh on 2007-07-04
Very good form, thanks for posting your fix! And grats, too.

---

### Post by SoulSmasher on 2008-02-19
wow thanks at last its ok now :)

it also may be 
monitoraspect=16:9 for actual widescreens
or
monitoraspect=16:10 for laptops

---

### Post by cyberdork33 on 2008-02-19
> **SoulSmasher said:**
> wow thanks at last its ok now :)

it also may be 
monitoraspect=16:9 for actual widescreens
or
monitoraspect=16:10 for laptopsNote that 915resolution should not be used anymore and the resolution issue with this graphics chipset is solved by using the 'Intel' driver rather than the i810 driver.

---

