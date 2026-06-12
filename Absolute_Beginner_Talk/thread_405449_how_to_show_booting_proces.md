---
title: "how to show booting proces?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by cele on 2007-04-09
How to remove that filling bar of Ubuntu 6.10 when booting and see exactly what he's doing? Is there some trick like hit this + that?

---

### Post by overdrank on 2007-04-09
> **cele said:**
> How to remove that filling bar of Ubuntu 6.10 when booting and see exactly what he's doing? Is there some trick like hit this + that?

Hi ESC works for me. Hope this helps!:guitar:

---

### Post by diatribe on 2007-04-09
gksudo gedit /boot/grub/menu.lst

remove all instances of 'splash' and 'quiet'

save and reboot

---

### Post by cele on 2007-04-09
it works but can it be saved somehow somewhere since it's 2 quick?
tnx

---

### Post by cele on 2007-04-10
Is there a way to save booting proces in a txt file? It's too quick on the monitor and I can't pause it.

---

### Post by mcduck on 2007-04-10
It's already saved by default into /var/log/boot. Also take a look at other log files inside /var/log.

By the way, you don't need to disable *both* quiet and splash. If you only remove the 'quiet' you'll get nice graphical splash with scrolling boot text ;)

---

### Post by cele on 2007-04-10
cool, i dodn't know that

---

