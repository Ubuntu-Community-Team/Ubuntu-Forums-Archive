---
title: "nothing in /etc/x11/xorg.conf"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by benduenga on 2006-07-11
I am brand new to linux.  I am trying to configure my computer and various threads refer to editing /etc/x11/xorg.conf with nano.  However, when I put the command
nano /etc/x11/xorg.conf 
in my terminal the editor starts, but there is nothing written.
thnks

---

### Post by tseliot on 2006-07-11
> **benduenga said:**
> I am brand new to linux.  I am trying to configure my computer and various threads refer to editing /etc/x11/xorg.conf with nano.  However, when I put the command
nano /etc/x11/xorg.conf 
in my terminal the editor starts, but there is nothing written.
thnks

Linux is case sensitive.

it's **X**11 and not x11

---

### Post by benduenga on 2006-07-11
thanks for the patience with a green newbie

---

### Post by taurus on 2006-07-11
And if you want to edit /etc/X11/xorg.conf, you need to be root so run it as
```

sudo nano /etc/X11/xorg.conf

```

---

### Post by louvros10 on 2007-10-21
I have the same problem after I tried to install compiz fusion.
I couldn't back up the file xorg.conf and now in restricted Drivers my Ati graphics card is not in use but enabled. The message I take is
Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid or does not exist.
Please help me!!!

---

### Post by Qwerty_ on 2007-10-21
Perhaps you can try

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by louvros10 on 2007-10-21
Thanks a lot.:)

---

