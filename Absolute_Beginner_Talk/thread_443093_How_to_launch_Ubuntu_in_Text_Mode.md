---
title: "How to launch Ubuntu in Text Mode?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by noo2bunto on 2007-05-14
Hello.  Is there a way to launch Ubuntu in text mode?  Thanks.

---

### Post by Najand on 2007-05-14
```
sudo rm /etc/rc2.d/S13gdm
```
and to make it work at startup again is:
```
sudo ln -s /etc/rc2.d/S13gdm /etc/init.d/gdm
```

---

### Post by coolzgeek on 2007-05-14
No no. its
sudo /etc/init.d/gdm stop

---

### Post by noo2bunto on 2007-05-14
Wow...That was fast.  Thanks for the replies.  Do we have a tie breaker?

---

### Post by Enverex on 2007-05-14
Just select "Recovery Mode" from Grub, it boots you into Runlevel 1 (init 1). I'm not sure if Ubuntu supports the "nox" kernel line Flag too which basically tells X not to start.

---

### Post by lakersforce on 2007-05-14
just press ctrl+alt+F1

---

### Post by MoxJet on 2007-05-14
> **coolzgeek said:**
> No no. its
sudo /etc/init.d/gdm stop

That wouldn't disable gdm to start up at rebooting.

---

