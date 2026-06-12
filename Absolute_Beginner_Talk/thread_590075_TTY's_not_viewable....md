---
title: "TTY's not viewable..."
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Graelb on 2007-10-24
I'm not sure if this is in the correct forum or not, but ... I'm running an nvidia geforce go  (i think it's a 6200), and whenever i go to ctrl+alt+F1-F6, i get a black screen. It's only when i'm using the restricted drivers for my video card. When i use the old vesa driver, it works correctly. I'm not sure what to do to fix it. any ideas?

---

### Post by tonyyarusso on 2007-10-25
Are you using a boot parameter other than vga=normal?  It's possible you may be running into the bug listed at [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)

---

