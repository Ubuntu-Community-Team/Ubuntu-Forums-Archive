---
title: "how come tuxcart runs so slow?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by outer_space on 2007-05-05
I am sure something is wrong because I have a decent vid card and this little 3d game slows it down to crap.  I did apt-get install nvidia-glx.  What else might I need to do?

---

### Post by aidanr on 2007-05-05
check /etc/X11/xorg.conf and in section "Device" make sure it's changed from "nv" to "nvidia" and then restart X (ctrl+alt+backspace)

---

### Post by outer_space on 2007-05-05
Its very pretty now thanks

---

