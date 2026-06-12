---
title: "Disabling the touch click on a laptop"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by g3k0 on 2007-01-13
I have an inspiron 6000.  I can click by touching the scroll pad on my laptop or by pressing the two buttons under it.  The touch on the scroll pad is far too sensitive so I would like to disable it.  It goes off all the time and opens links I do not want to open.  Can someone tell me how to fix this?

Thanks

---

### Post by Vorian on 2007-01-13
Nice Laptop!8)

This will do the trick....
```
sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"
```

*EDIT

Then restart your laptop :)

---

### Post by g3k0 on 2007-01-13
hmm this seems to disable the scroll bars on the touch pad but not the actual clicking feature on mine.

---

