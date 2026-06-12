---
title: "enable wireless at system start"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by davidsotl on 2007-10-20
I know this must be a "absolute beginner" question. I'm very happy that I got my wireless up on Ubuntu, but the problem is that every time I reboot, I have to type sudo modprobe ndiswrapper to re-enable my wireless, I know there must be a way, one line in a config file somewhere to solve this problem, I just don't know how, could anyone help me?

---

### Post by catfacts on 2007-10-21
Ok go to System > Prefs > Sessions Choose add type in the line you need and save it. Since it is sudo it may do something weird though. Does it work without the sudo? try it first that way.

---

### Post by HokeyFry on 2007-10-21
try this in a terminal
```
sudo -s
echo 'ndiswrapper' >> /etc/modules
```

then reboot

---

### Post by davidsotl on 2007-10-21
thank you guys for helping, the second one worked!

---

