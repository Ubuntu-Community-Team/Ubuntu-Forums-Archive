---
title: "Fiesty not letting me enable restricted driver"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by reidamd on 2007-04-27
I am trying to enable my nvidia drivers through the restricted driver manager, and I click to enable it and it stays as not in use. What's going on here?

---

### Post by lamalex on 2007-04-27
did you enable and then restart?

---

### Post by reidamd on 2007-04-27
when I try to enable, the enable check box stays unchecked after accepting. Let me try restart to see if it helps

---

### Post by reidamd on 2007-04-27
After rebooting still says not in use. When I enable it, it greys out a second then stays as unchecked. I'm stumped, is there a way do try this through the terminal rather than using the restricted drivers manager? After I try to enable it doesnt even prompt me to reboot.

---

### Post by lamalex on 2007-04-27
try looking here [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-7f830fe17ae6da7c546decbb10c32ff61471258e](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-7f830fe17ae6da7c546decbb10c32ff61471258e)

---

### Post by reidamd on 2007-04-27
Which part will show me how to use terminal to install driver? I'm very new to linux, few hours, so the less technical, the better, thanks.

---

### Post by reidamd on 2007-04-27
I reinstalled with the 32 bit version, I wanted to use WINE anyhow, and prefer not to use the work around. Seems the 64 bit version doesnt offer enough performance to outweigh it's problems, at least for what I need it for.

---

### Post by Najand on 2007-04-27
Try to install "nvidia-xconfig" manually:
```

$ sudo apt-get install nvidia-xconfig

```
and then restart your computer and check the restricted box again.

---

