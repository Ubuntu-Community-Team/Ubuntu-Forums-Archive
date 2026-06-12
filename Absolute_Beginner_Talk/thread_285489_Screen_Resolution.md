---
title: "Screen Resolution"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by big_bad_brad on 2006-10-26
I just got a new monitor and can't get a better resolution than 640x480.
With my old monitor sometimes it would start ubuntu in this resolution and wouldn't give me the option to change it, I would restart and everything was fine.  Now with the new monitor it doesn't seem to matter how many times I resart it is just stuck at 640x480.  Any help?
Thanks

---

### Post by DSn0wMan on 2006-10-26
You probably need to reconfigure xserver.

```
sudo dpkg-reconfigure xserver-xorg
```

or just edit /etc/X11/xorg.conf and restart xserver

---

### Post by big_bad_brad on 2006-10-26
Thanks,
That helped.

---

### Post by Sakryn on 2006-10-27
I just wanted to say thank you as well, I have been working trying to get anything above 640x480 resolution and this finally worked.

---

