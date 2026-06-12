---
title: "Ubuntu 8.05 and MacbookPro last generation"
date: 2008-05-08
forum: Apple Hardware Users
---

### Post by emmeelle on 2008-05-08
Hi,
I installed ubuntu 8.05 on my new macbook pro (last generation) but I have a lot of problem and I have not found the solution in other threads.

The problems are:
-I can't use bluetooth: I don't see other device and they don't see me, this is "hcitool scan" output:

Scanning ...
Inquiry failed: Connection timed out


-Special keys don't work (sound volume, brightness, etc) also if I use Fn key.
I installed Pommed but never changed.

-\| and <> keys are swapped!!
I've found a script ti solve this problem but it use xkbset and I can't use it:

$ xkbset m
XKB not supported for display :0.0

I hope somebody can help me and I clarify that I'm not a very expert user.

---

### Post by emmeelle on 2008-05-08
I solved problem about swapped keys (now xkbset works!!!) and bluetooth ( sudo hciconfig hci0 reset) but problem about special keys, Fn and pommed remains...

---

### Post by maddojf on 2008-05-08
Are you using the 32 bit or the 64 bit version?

---

### Post by Super Jamie on 2008-11-14
> **emmeelle said:**
> $ xkbset m
XKB not supported for display :0.0

Run this first:
```
setxkbmap -layout us
```

---

### Post by Kooothor on 2008-11-14
Why don't install 8.10 ?
The kernel is more recent
Then if you use dkms and applesmc kernel module, all will be fine !

---

