---
title: "press the power button on the computer"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-02-17
how can i modify the settings so that when i press the power button on the cpu ,it shuts down the computer, rather than just showing the quit dialog?

---

### Post by glotz on 2007-02-17
I think this is controlled by the BIOS. So, boot your system and during the boot it should say something like "Press Del to enter CMOS setup".

---

### Post by annda on 2007-02-17
in my experience, if you want to make sure your computer shuts down, press the button for 5-10 seconds.

---

### Post by kinematic on 2007-02-17
you can use gconf editor to do that.
applications>system tools>gconf>apps>gnome power manager.
you'll see a listing of valid options for each action wich includes "shutdown" when you hit the power button.

---

### Post by Skidpad on 2007-02-17
You can also access it through System>Preferences>Power Management>General.

---

### Post by linux_kid on 2007-02-17
How long did you hold the button down for?

---

### Post by cohort on 2007-02-26
> **kinematic said:**
> you'll see a listing of valid options for each action wich includes "shutdown" when you hit the power button.
I don't see 'shutdown'.  I see 'suspend' and 'hibernate', neither of which I want.  I want to power down.

---

### Post by urk_nono on 2007-02-26
**sudo shutdown now** should do the trick..

---

