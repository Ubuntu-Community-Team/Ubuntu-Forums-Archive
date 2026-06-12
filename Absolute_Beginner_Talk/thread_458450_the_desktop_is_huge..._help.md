---
title: "the desktop is huge... help"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by ToNeZ on 2007-05-29
i install feisty today and its all huge... i try to configure it but the resolution only gets to 800x600

i have vista and i can get 1028 resolution... how i correct this, dont like it this huge... i used edgy for a while and it wasnt this hige

---

### Post by Ek0nomik on 2007-05-29
Try running this first; open a terminal and type:

```
dpkg-reconfigure -phigh xserver-xorg
```

Use spacebar to select items/resolutions

---

### Post by ToNeZ on 2007-05-29
when i type it  this is what it says... "reconfigure must be run as root"

---

### Post by DJ Wings on 2007-05-29
Add a "sudo " in front of it.

---

### Post by Ek0nomik on 2007-05-29
Sorry, I am at work and they only run Windows.  ;)  sudo will do the trick as he mentioned.

---

### Post by ToNeZ on 2007-05-29
i did it and this is wut it tells me...
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070529175416

---

### Post by Ek0nomik on 2007-05-29
Run it again and you should be fine.

Or if you have a choice, just accept.

---

### Post by ToNeZ on 2007-05-29
it only says that i cant choose nothing, i type again " sudo dpkg-reconfigure -phigh xserver-xorg" and tells me the same thing

---

### Post by Xappe on 2007-05-29
remove the -phigh option and you should get the setup going...

---

### Post by ToNeZ on 2007-05-29
> **Xappe said:**
> remove the -phigh option and you should get the setup going...

thanx man help me a lot...it worked

---

