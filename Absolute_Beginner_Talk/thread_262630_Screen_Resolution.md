---
title: "Screen Resolution"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by sda80 on 2006-09-21
Hello, I just installed Ubuntu a few minutes ago...So far it's awesome. I have a small issue though:

My monitor will support up to 1280 by 1024 but yet the highest option on the screen resolution is "1024x768".

Is there a tool similar to Fedora's "system-config-display". If not, does anyone know how I can change this?

thanks.

---

### Post by Qrk on 2006-09-21
Use the command

```
sudo dpkg-reconfigure xserver-xorg
```

You may need to select a different video driver to support your native resolution than the one Ubuntu selected by default.

---

### Post by sda80 on 2006-09-22
That worked, Thank You!
:D

---

