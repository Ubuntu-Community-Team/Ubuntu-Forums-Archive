---
title: "macbook4.1 ubuntu8.10 configuring wireless and others"
date: 2009-02-12
forum: Apple Hardware Users
---

### Post by pr0ject_2501 on 2009-02-12
I have looked at [https://help.ubuntu.com/community/MacBook4-1/Intrepid](https://help.ubuntu.com/community/MacBook4-1/Intrepid)

Wireless (AirPort)
I see no components under Systems -> Hardware Drivers, so it is impossible to simply activate "Broadcom STA wireless driver"

Touchpad (appletouch)
I have done what it says but nothing is different.

Have not attempted anything else.

---

### Post by cyberdork33 on 2009-02-12
please check that the "wl" driver is loaded. You can do this by running "lsmod" in a terminal.

For the touchpad to work right, you will probably need to install some packages from the mactel-support PPA and make sure there is no touchpad configuration section in your xorg.conf file if you are trying to use the fdi file.

---

### Post by pr0ject_2501 on 2009-02-20
I do not see "wl" in the list, so how do I load the driver?

---

### Post by cyberdork33 on 2009-02-20
> **pr0ject_2501 said:**
> I do not see "wl" in the list, so how do I load the driver?
First, make sure to unload other drivers that may conflict:
```
sudo modprobe -r b43
sudo modprobe -r b43legacy
```

then load the wl module:
```
sudo modprobe wl
```

then add 'wl' to /etc/modules so that it loads automatically on startup.

---

### Post by pr0ject_2501 on 2009-05-08
When trying to load "wl" with:
sudo modprobe wl

it returns:
FATAL: Error inserting wl (/lib/modules/2.6.24-19-generic/volatile/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by cyberdork33 on 2009-05-08
can you check dmesg after you do that?

---

