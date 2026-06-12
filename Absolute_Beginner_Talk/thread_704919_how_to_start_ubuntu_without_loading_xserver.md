---
title: "how to start ubuntu without loading xserver?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by rmx on 2008-02-22
hello

Need to install fglrx 8.2 and read somewhere that I need to do it in text mode, before xserver load.

Any hints?

thanks

Rmx

---

### Post by kool_kat_os on 2008-02-22
do you need the xserver?

---

### Post by p_quarles on 2008-02-22
Two ways to do this:
1) After the BIOS gives control to GRUB, press escape to see the boot menu. Choose the Recovery/Single User Mode option to boot up into a root console, without X.

or

2) After the main login screen comes up, choose "options" and select a console login. Then, stop the GUI:
```
sudo /etc/init.d/gdm stop
```

---

### Post by zabien1970 on 2008-02-22
from recovery mode you can restart your computer with 

shutdown now -r

(the -r tells it to restart)

---

### Post by rmx on 2008-02-23
> **p_quarles said:**
> Two ways to do this:
1) After the BIOS gives control to GRUB, press escape to see the boot menu. Choose the Recovery/Single User Mode option to boot up into a root console, without X.

or

2) After the main login screen comes up, choose "options" and select a console login. Then, stop the GUI:
```
sudo /etc/init.d/gdm stop
```

thanks for your help, 

1) is it ok to install a drive in recovery mode?
I mean, isn't it a different kernel?

2) but if I see the login screen I guess I'm already on a graphical environment, which probably means I'm using graphical drive.

---

### Post by p_quarles on 2008-02-23
> **rmx said:**
> thanks for your help, 

1) is it ok to install a drive in recovery mode?
I mean, isn't it a different kernel?
It's not a different kernel (normally; the only exception would be if you had set it up that way). It's the same kernel with the "single" argument passed to it during boot.

> 2) but if I see the login screen I guess I'm already on a graphical environment, which probably means I'm using graphical drive.
Yes, but the command I gave you will shutdown that graphical environment. There is also a way of getting the GUI to not start automatically, but that would be more work in the long run, as you would have to re-enable it after installing the driver.

---

### Post by andrewjoy on 2008-02-23
Alternativly you could do a ctl + alt + backspace when logged into gnome / kde ect and then use the

```
sudo /etc/init.d/gdm stop
```

---

