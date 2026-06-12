---
title: "Monitor goes into standby mode / Not Wanted!"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by neuroplasma on 2006-11-18
My monitor will go into standby mode after a certain period of inactivity, this messes with certain apps I run. All of the power management settings are turned off, including the monitor settings.

I also ran "xset -dpms" at the behest of a poster on another forum, but to no avail.

Please help, it's driving me insane!

---

### Post by m_bridge on 2007-05-07
this seems to do the job
```
xset -display :0 dpms force on
```

---

