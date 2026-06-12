---
title: "No Sound 7.10 Compaq C700"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by apurvas84 on 2007-11-07
Just installed Ubuntu 7.10 for the first time. No sound. Tried Googling.

Tried this command and got the output:

 lspci -n | grep `lspci | grep -i audio | awk '{print $1}'`
00:1b.0 0403: 8086:284b (rev 03)


Somebody please help.

Can't wait to listen to Johnny Cash!

---

### Post by vladan.b on 2007-11-08
If you have Intel-based sound card on your laptop, you may try this: Terminal > gedit /etc/modprobe.d/alsa-base, and add the line below at the end of the file.  Save, reboot and hope.
```

options snd-hda-intel model=auto

```

---

### Post by vladan.b on 2007-11-08
credit goes to
```

http://ubuntuforums.org/showthread.php?t=416207

```

---

