---
title: "Trackpad issues  on PB 12&quot; (post feb05)"
date: 2006-10-22
forum: Apple PPC Users
---

### Post by chimaera on 2006-10-22
hi, 
i cannot get the trackpad on my powerbook 12" to work reliably. i'm using edgy, all packages up-to-date. 

i'm using the appletouch/synaptics drivers and tried different configurations for synaptics found throughout this forum and the interwebs, but all i get very choppy and erratic movements. the cursor jumps around, stops moving at all for some seconds or moves in the opposite direction when taking my finger of the tab. impossible to use that way. any ideas where to look?

---

### Post by joonahoi on 2006-10-23
I'm seeing similar behaviour after waking my PB up from sleep, for me it seems like the problem lies in appletouch driver, and not synaptics but I'll try to look more into it.

---

### Post by joonahoi on 2006-10-23
Did you get it sorted out? For me, it seems like the problem went away.

I found out the problem is not synaptics, as touchpad driver itself seems to be sending erratic signals.

Anyway, this is how I got the touchpad working after it started to behave like an ***: 

```

sudo modprobe -r appletouch
sudo modprobe appletouch

```

---

