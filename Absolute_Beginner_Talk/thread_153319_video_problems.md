---
title: "video problems"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by rmvg on 2006-03-31
I have install ubuntu on a newer intel/ati motherboard 910 chipset i think and ubuntu will not but xorg get tons of errors can only login in text mode.

---

### Post by andrewsawyer on 2006-03-31
When you login in text mode, try reconfiguring the xorg by typing:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Let me know if this works.

---

### Post by Mustard on 2006-03-31
With the ati situation, I would suspect that you would need to set up xorg to use 'vesa' drivers to get a gui, and from there you could try installing the ati drivers.

---

