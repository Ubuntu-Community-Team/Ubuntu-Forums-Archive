---
title: "[SOLVED] Keyboard backlight does not work"
date: 2008-12-27
forum: Apple Hardware Users
---

### Post by hanzomon4 on 2008-12-27
I've installed the hal-applesmc package and applesmc is in /etc/modules. I'm on a macbook pro 3.1 running intrepid. I've had intrepid on here before and it worked great. I took it off for a while and decided to reinstall, now nothing works the way it did a few months ago. The trackpad fdi config didn't work, resume doesn't work, keyboard backlight... Many of the instructions I followed the first time don't work anymore.

What happened?

---

### Post by hanzomon4 on 2008-12-27
I fooled around with some track pad settings and my acpi-support file(trying to get resume to work), rebooted and the keyboard lit up like a Christmas tree.

---

### Post by hellmitre on 2009-02-10
Do you know which settings you fooled around with?

---

### Post by hellmitre on 2009-02-10
I figured it out: on MacBook Pro 3,1 versions, you simply remove the MacBook Pro 3,1 entries from /usr/share/hal/fdi/policy/10osvendor/10-macbookpro-utils.fdi, then open gconf-editor, go to apps --> gnome-power-manager and select backlight. Adjust the settings from 100 and 50 (the defaults, I believe) to 0 and 0 if you don't want it turning on every time the power state changes.

---

