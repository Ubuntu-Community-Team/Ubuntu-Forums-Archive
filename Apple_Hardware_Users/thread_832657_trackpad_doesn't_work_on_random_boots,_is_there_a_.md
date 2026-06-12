---
title: "trackpad doesn't work on random boots, is there a command to reload.. ?"
date: 2008-06-17
forum: Apple Hardware Users
---

### Post by dustynus on 2008-06-17
Rebooting fixes, but it's kinda a nuissance when I boot and then have no mouse.

Is there a command I can do to reload the trackpad modules?

---

### Post by cyberdork33 on 2008-06-17
> **dustynus said:**
> Rebooting fixes, but it's kinda a nuissance when I boot and then have no mouse.

Is there a command I can do to reload the trackpad modules?
It would be 100x more helpful if you posted what hardware you are on :)

Are there any messages in dmesg that seem to indicate a problem with the trackpad?

---

### Post by dustynus on 2008-06-18
I'm on a macbook 2,1.
running hardy 8.04

Same thing happened in gutsy as well, it just happens on occasion.
I'm also using volanin's trackpad package from:
[http://ubuntuforums.org/showthread.php?t=790589&highlight=dustynus](http://ubuntuforums.org/showthread.php?t=790589&highlight=dustynus)

It seems like it's just not loading the trackpad modules or something.

I'll post a dmesg next time it happens.

---

### Post by cyberdork33 on 2008-06-18
when it doesn't work, make sure that appletouch is loaded.

---

### Post by idrake on 2008-06-19
> **dustynus said:**
> Rebooting fixes, but it's kinda a nuissance when I boot and then have no mouse.

Is there a command I can do to reload the trackpad modules?

I know this problem. It occurs on my Mac if I dissable the autostart of gdm on bootup and start gdm or X11 later on manually.

Just reload the appletouch driver:
```

sudo modprobe -r appletouch

sudo modprobe appletouch

```

If the your mouse is unusually slow afterwards, changing to the terminal (by strg - alt - fn -f1 / strg - alt - f5) and back to X11 (strg - alt - fn - f7) fixes this for me.

---

### Post by dustynus on 2008-06-24
Thanks, that's what I was looking for, I wasn't sure what module is was that took care of the trackpad.

---

