---
title: "Backlight on MBPro only 5 settings, high pitched sound, changes randomly"
date: 2009-03-09
forum: Apple Hardware Users
---

### Post by everfine on 2009-03-09
The backlight on my MBPro 4,1 with 8.10 only goes about a quarter of the way on the bar, makes a high pitched sound when up high, and will dim sporadically. Anyone know how to fix?

---

### Post by cyberdork33 on 2009-03-09
are you using the documentation for your mac?
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

Which version of Ubuntu are you using?

The dimming is supposed to occur after a certain period of time to conserve battery power. It should, however, go back to normal if you try to use the mouse / keyboard again.

---

### Post by Tu1J4kXk8NUhMz on 2009-03-09
I had this problem when I first installed Hardy. Ubuntu uses a light sensor (the same it uses for your keyboard, I suspect) in the MBP to adjust screen brightness, and in Hardy it would adjust the brightness until the screen was black. Intrepid is much better about that.

If it bugs you, go into gconf-editor

apps > gnome-power-manager > backlight >

There are three checkboxes, I think. Just look for the one which dims the backlight.

---

### Post by _mario_ on 2009-03-10
> **everfine said:**
> The backlight on my MBPro 4,1 with 8.10 only goes about a quarter of the way on the bar, makes a high pitched sound when up high, and will dim sporadically. Anyone know how to fix?

are you referring to the display backlight? then there should be more than 4 or 5 steps available. what does the following command output?

```
lshal -u `hal-find-by-capability --capability laptop_panel`
```

ciao,
Mario

---

