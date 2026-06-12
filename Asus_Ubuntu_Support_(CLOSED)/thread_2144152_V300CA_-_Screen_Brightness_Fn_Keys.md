---
title: "V300CA - Screen Brightness Fn Keys"
date: 2013-05-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by tabsterleir on 2013-05-11
Hi all,

So i've recently installed Kubuntu 13.04 on my Vivobook V300 and i've just noticed a strange bug with my keyboard brightness FN keys. If I use the Brightness Down button it works as expected, however if I use the Brightness Up key it seems to scroll through 3 different brightness levels before returning to the first and repeating the process. It doesn't actually increase the brightness as its meant to. I can easily return the brightness to full by using the power management tray icon but i'd like to be able to use my keys as normal as well. Does anyone have any ideas?

---

### Post by tabsterleir on 2013-05-11
[FONT=arial]Solved! I added [COLOR=#333333]*acpi_osi='!Windows 2012' to /etc/default/grub and ran sudo update-grub and all was well :D*[/COLOR][/FONT]

---

