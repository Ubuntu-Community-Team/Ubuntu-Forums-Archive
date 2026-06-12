---
title: "problem after install"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by sohei on 2006-04-01
I have installed Ubuntu 5.10 without incident and rebooted, I also login w/o incident and then nothing. Well nothing but a amber colored screen with nothing on it but a functioning mouse cursor.  The system would not do a reboot so I had to do a hard power down.  Powering it back up did not solve the problem.

Any help would be appreciated.

---

### Post by aysiu on 2006-04-01
Try this:

1. Press Control-Alt-F1
2. Log in
3. Type ```
sudo dpkg-reconfigure xserver-xorg
```
4. Answer the questions as best you can, being as conservative as possible for screen resolution
5. Press Control-Alt-F7
6. Press Control-Alt-Backspace

---

