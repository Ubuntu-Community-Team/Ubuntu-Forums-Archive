---
title: "Installing error dpkg"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by spykid33 on 2007-05-28
AFter enabled desktop effects and used compiz manager and go to install a program I get this error: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Please help me.

---

### Post by abn91c on 2007-05-28
try running that command in a root shell terminal, I had similar problem and it fixed it.

---

### Post by meng on 2007-05-28
Either in a root shell or else you can do this in a regular terminal:
sudo dpkg --configure -a
(enter user password when prompted, it will NOT echo to screen)

---

