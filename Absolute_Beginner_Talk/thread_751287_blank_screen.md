---
title: "blank screen"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by bdumont on 2008-04-10
please help new to xunbuntu.  i was messing around with the window graphics and checked a box for some kind of wrapping?  have no idea what i did but the toolbars went away and went i rebooted the screen goes tan and doesnt load after login.   thanks please help!

---

### Post by mali2297 on 2008-04-10
Go to a virtual console by pressing **Ctrl+Alt+F2**. Login, then type
```

rm -rf .config/xfce4
sudo dpkg-reconfigure -phigh xserver-xorg

```
Hopefully, this will reset your configuration. 

Go back to the GUI by pressing **Ctrl+Alt+F7** and then restart it with **Ctrl+Alt+Backspace**.

---

### Post by bdumont on 2008-04-10
thank you!!!! thank you, thank you, thank you!  problem solved

---

