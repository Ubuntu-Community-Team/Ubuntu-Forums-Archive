---
title: "power management - monitor switches off!!"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by verbatim210 on 2006-06-10
system>pref>power management....  
all settings turned to **never** switch off.  
but the monitor still switches off!

why?

---

### Post by dglock on 2006-06-10
you can turn it off by going to /etc/X11/xorg.conf, comment out all lines that contain "DPMS".

don

---

### Post by verbatim210 on 2006-06-10
so do i just delete the **dpms** inside the quotation marks?

---

### Post by Dr. Nick on 2006-06-10
Have you checked your bios power managemt features, I am not sure if ubuntu will override your bios settings, But I know alot of bios have options for monitor off.

---

### Post by verbatim210 on 2006-06-12
hey Dr.Nick,

i went to bios and i saw:
power management - user defined
video off after standby

im not too fussed about this "problem" i spose, more curious than fussed.

---

