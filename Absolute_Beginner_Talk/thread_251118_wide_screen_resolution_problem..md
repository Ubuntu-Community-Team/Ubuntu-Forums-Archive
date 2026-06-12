---
title: "wide screen resolution problem."
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2006-09-05
hey guys, i just got back from the store with a brand new hd widescreen monitor. it sais the recomended resolution is 1440x900 @ 60HZ. 

 i dont have a selection for 1440x900 in the system/prefs/screen resolution tab. is it possible to add this some how??  let me kno! thanks guys:-D

---

### Post by bodhi.zazen on 2006-09-05
Try:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```

If that fails you will need to edit xorg.conf by hand.

---

### Post by Seine on 2006-09-05
I had this question about 14 hours ago. :D 

See [http://www.ubuntuforums.org/showthread.php?t=250502](http://www.ubuntuforums.org/showthread.php?t=250502)

---

### Post by da1nonlymikeo on 2006-09-05
okay i got the resolution to show up in the selections. but when i chose it it like centers and cuts the left and rite sides off. like making my monitor non-widescreen lol.

---

### Post by bodhi.zazen on 2006-09-05
Are the other resolutions OK?

I am not familiar with your monitor (model # please), but my monitor has knobs (buttons actually) to adjust the size and location of the screen. If other resolutions are OK try adjusting the monitor itself.

If you think the problem is with X, post xorg.conf (/etc/X11/xorg.conf)

---

