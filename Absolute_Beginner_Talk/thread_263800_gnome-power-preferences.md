---
title: "gnome-power-preferences"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by Ephilei on 2006-09-23
How do I prohibit ubuntu from sleeping? I've turned sleeping off in the GUI (gnome-power-preferences) but no go. Or even better, if Ubuntu can just be woken when contacted via remote desktop or samba file sharing, it can sleep all it likes. 

Thanks

---

### Post by blx_286 on 2006-09-23
> **Ephilei said:**
> How do I prohibit ubuntu from sleeping? I've turned sleeping off in the GUI (gnome-power-preferences) but no go. Or even better, if Ubuntu can just be woken when contacted via remote desktop or samba file sharing, it can sleep all it likes. 

Thanks

If you are talking about the monitor sleeping, then this may help [http://ubuntuforums.org/showthread.php?t=246688&highlight=gnome+power+management](http://ubuntuforums.org/showthread.php?t=246688&highlight=gnome+power+management)

There is also an monitor option in xorg.conf, which is Option "DPMS". Comment this out by adding a # to the start of the line.

---

### Post by Ephilei on 2006-09-24
Yeah, adding those lines to xorg.conf worked fine. Thanks!

---

### Post by Ephilei on 2006-12-08
I applied those changes a while ago and they worked until I upgraded to Edgy (fresh install). I did exactly as before, changing xorg.conf, but there's no affect this time. I need this desperately because I need to back up from another computer and the transfer takes about 24 hours.

---

