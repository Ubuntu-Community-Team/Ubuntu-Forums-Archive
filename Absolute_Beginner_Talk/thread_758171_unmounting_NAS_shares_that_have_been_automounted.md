---
title: "unmounting NAS shares that have been automounted"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by myotis on 2008-04-17
This may be a silly question but when I automount shares on a NAS (QNAP) using fstab and cifs at boot, do I need to unmount them before shutting down.

It seems I can only unmount them as root, and this means going into the terminal. 

I assume that either I don't need to unmount them, or that there is a cleverer way of doing this.

Thanks,

Graham

---

### Post by zackf on 2008-04-17
Graham,

Nah, it's cool. I have a similar setup and don't unmount before shutting down.

---

### Post by myotis on 2008-04-18
> **zackf said:**
> Graham,

Nah, it's cool. I have a similar setup and don't unmount before shutting down.


Thanks, I did wonder if that was the case, as they were mounted via fstab, but I also was under the impression that you needed to unmount volumes before switching off.

Glad to see that isn't needed.

Graham

---

### Post by joshrobinson on 2008-04-18
they unmount automatically on shutdown

---

### Post by myotis on 2008-04-18
> **joshrobinson said:**
> they unmount automatically on shutdown

Thanks, I did think that might be the case.

Graham

---

