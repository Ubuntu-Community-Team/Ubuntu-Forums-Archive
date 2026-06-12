---
title: "mouse is a black THINGY...have searched, what to do?"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by alinuxfan on 2006-01-10
my mouse pointer looks like ARSE.  I don't know what the heck to do...do I need to go somewhere and change a setting?  I just switched from Mandrake and I had no problems there...any ideas?

---

### Post by alinuxfan on 2006-01-10
ok, I think I figured it out...I have a ATI rage 128 Pro and I didn't have the drivers installed....I changed my xorg.conf to the right driver and now the pointer is white and seems to be working

---

### Post by alinuxfan on 2006-01-10
ok, I think I figured it out...I have a ATI rage 128 Pro and I didn't have the drivers installed....I changed my xorg.conf to the right driver and now the pointer is white and seems to be working

ok, now it isn't #D supported...I wish I would have saved my xorg file from mandrake

---

### Post by az on 2006-01-10
The rage128 driver is not entirely stable.  There is a memory leak.  You can workaround the problem by either dissabling dri in your config or using the sw-cursor option

Section "Device"
        Identifier      "ATI Technologies, Inc. Rage 128 PP/PRO (TMDS Xpert 128)"
        Driver          "ati"
        Option         "sw_cursor"      "true"
        BusID           "PCI:0:8:0"
EndSection

---

### Post by alinuxfan on 2006-01-10
thanks, that works with AGP too?

---

