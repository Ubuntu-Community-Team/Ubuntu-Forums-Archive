---
title: "going from dhcp to static network, resolv.conf problem"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-10-16
I use during the day a wireless network using dhcp, then when I come home at night I use my own wireless network but got setup for static.

problem is the /etc/resolv.conf file gets overwritten by the dhcp, is there any way I can then rewrite the file for my static IP address setup?

I've tried the following in my /etc/network/interfaces file but doesn't work.
```


auto ra0
iface ra0 inet static
        address 192.168.0.177
        netmask 255.255.255.0
        gateway 192.168.0.1
        dns-nameservers 192.168.0.1
#
        pre-up ifconfig ra0 up
        pre-up iwconfig ra0 mode Managed
        pre-up iwconfig ra0 essid dlink


        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK=xxxxxxxxxx
        cp /etc/resolv.conf.bk /etc/resolv.conf
        pre-up ifconfig ra0 up

```

---

### Post by ZeroVerteX on 2007-10-16
Try copying your resolv.conf last. When you "pre-up ifconfig ra0 up" it's probably overwriting resolv.conf again. Example below.

```

        pre-up ifconfig ra0 up
        cp /etc/resolv.conf.bk /etc/resolv.conf

```

---

### Post by PetePete on 2007-10-17
thansk for answer, but that didn't work.

dont think you can put commands in /etc/interfaces file like that

---

### Post by Kensey on 2007-10-17
> **PetePete said:**
> thansk for answer, but that didn't work.

dont think you can put commands in /etc/interfaces file like that

Try putting "pre-up" in front of the line that copies your resolv.conf, just like the other lines.

[Edited to add: and it should still be the last line, like the other poster said.]

---

