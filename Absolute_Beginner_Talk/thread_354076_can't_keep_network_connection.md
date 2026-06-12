---
title: "can't keep network connection"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by yanqui on 2007-02-05
Ubuntu seems to be working fine for the most part, except for my network/internet connection.  It's okay when I start up, but eventually drops the connection completely.  Where should I start to troubleshoot?

---

### Post by yanqui on 2007-02-06
I wanted to give this thread a bump because my Windows box keeps teh same connection consistently; the Ubuntu is installed on a usb hard drive.  We have serious internet issues here, is it possible that if the internet is not available for a period of time that Ubuntu severs the connection and I have to reboot to reconnect?

---

### Post by RomeReactor on 2007-02-06
Hi. I'm not sure if this is the problem, but it might help if you disable ACPI. In a terminal write

```
sudo gedit /boot/grub/menu.lst
```

then, when gedit opens, write

```
acpi=off
```

between **"### BEGIN AUTOMAGIC KERNELS LIST"** and **"## DO NOT UNCOMMENT THEM, Just edit them to your needs"**. Save and reboot.

---

### Post by yanqui on 2007-02-09
It doesn't seem to have worked.  I'll keep looking.

---

