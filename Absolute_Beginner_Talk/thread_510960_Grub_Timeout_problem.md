---
title: "Grub Timeout problem"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Industrio on 2007-07-27
I am new to Linux. I just installed Ubuntu.I want to disable the grub time out.I have read some related links and it says go to grub.conf and set time out=0. I want to know how to get there and do it.Plz help

---

### Post by kngunn on 2007-07-27
It's in \boot\grub\menu.lst (that's an LST at the end, not the number one.)

```

sudo gedit /boot/grub/menu.lst

```

Just change the "timeout" line, save, and restart.

---

