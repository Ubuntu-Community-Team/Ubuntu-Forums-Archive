---
title: "System&gt;Pref&gt;ScreenRes not showing values listed in xorg.conf"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by lirael on 2006-12-06
So I went and changed the xorg.conf to have higher resolution values than what's offered originally (the highest being 1024x768) and even after rebooting they still don't show up in System>Preferences>Screen Resolution. What did I need to do to fix this?

---

### Post by CatKiller on 2006-12-07
You probably need to add in the HorizSync and VertRefresh refresh rate ranges for your monitor. Check your monitor manual or the manufacturer's website for the numbers, and then put them into the Monitor section of your xorg.conf.

Unless you're using the **vesa** driver, or course. That won't ever go higher than that, as I understand it.

---

### Post by lirael on 2006-12-07
It worked when I switched to 16bit rather than 24.

---

