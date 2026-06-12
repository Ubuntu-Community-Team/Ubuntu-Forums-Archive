---
title: "SSH question"
date: 2009-02-03
forum: Assistive Technology &amp; Accessibility
---

### Post by aliciapg on 2009-02-03
Is there a way you can turn up the volume on a computer over ssh?

---

### Post by lloyd_b on 2009-02-03
> **aliciapg said:**
> Is there a way you can turn up the volume on a computer over ssh?

Try running "alsamixer" via ssh.  Exactly *which* of the available controls you want to be adjusting depends on exactly what it is you want to change the volume on ("PCM" works for most applications).

(Left/right arrow keys to select the channel, up/down arrows to change volume, "<ctrl> c" to exit).

Lloyd B.

---

### Post by aliciapg on 2009-02-05
Thanks! That helped a lot!

---

### Post by aliciapg on 2009-02-06
Okay, I got that, now is it possible to pause music/change songs and stuff in rhythmbox over ssh? I was using the GUI, but I would prefer to use a command.

---

