---
title: "x server problem please help urgent"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by maneesh77 on 2006-09-26
at last use I installed macox theme and glass fonts. now when I booted , it says x server failed to start. when i click on diagnose problem it says some stuff about which I have no idea. Please help all my files are there as I just made the complete switch from xp 2 days ago

---

### Post by bodhi.zazen on 2006-09-26
Start with typing the command:
```
sudo dpkg -reconfigure -phigh xserver-xorg
```

And re-start x
```
sudo gdm
```

If that does not work, I do not know either.

Perhaps if yo were to post those error messages.

---

