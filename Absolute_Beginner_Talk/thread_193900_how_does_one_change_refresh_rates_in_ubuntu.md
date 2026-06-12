---
title: "how does one change refresh rates in ubuntu?"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-10
tried adding the vertical and horizontal refresh rates in the xorg.conf file but i still can't change the refresh rates

---

### Post by shamrock_uk on 2006-06-10
[QUOTE=lime4x4]tried adding the vertical and horizontal refresh rates in the xorg.conf file but i still can't change the refresh rates[/QUOTE]

You took the values from your monitor manual, yes? It might be worth doing the whole config from scratch:

```
sudo dpkg-reconfigure xserver-xorg
``` to ensure the format is correct. Select 'medium' or 'advanced' when it comes to your monitor.

What happens when you try changing it by the resolution changer? (System -> Prefs -> Screen Res)

---

### Post by lime4x4 on 2006-06-10
nothing when i hit the drop down arrow nothing shows up

---

### Post by lime4x4 on 2006-06-10
also when i try your command i get an error about xserver not a valid command

---

### Post by Dr. Nick on 2006-06-11
the command
sudo dpkg-reconfigure xserver-xorg

should work from a terminal. run this from a terminal and post the outpt here, or just compare with my example for setting refresh rates.

cat /etc/X11/xorg.conf

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection
```

---

