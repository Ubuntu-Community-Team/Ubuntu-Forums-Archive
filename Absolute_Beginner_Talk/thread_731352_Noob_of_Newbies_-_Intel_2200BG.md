---
title: "Noob of Newbies - Intel 2200BG"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by kanatejr on 2008-03-21
Hi!

Just got Ubuntu on today, after 5 tries... Don't know what was wrong with my CD-R.

Dual Boot; Hardware:
VAIO S57SP/B

Only thing that doesn't seem to work so far is the WiFi. lshw shows *-network : 1 UNCLAIMED but info of the card shows up.

Its Intel PRO/Wiress 2200BG
physical id: b
capabilities: om bus_master cap_list
config: latency =32 maxlatency=24 min=3

Any help?

Thanks a lot!!!

KanateJR

---

### Post by Hospadar on 2008-03-21
could you post the outputs of "lspci" and "lsmod" also "iwconfig" would be helpful

---

### Post by Bachstelze on 2008-03-21
Please paste the output of

```
sudo iwconfig
lsmod | grep ipw

```

---

### Post by kanatejr on 2008-03-21
```
sudo config
```

```

lo       no wireless extensions.
eth0   no wireless extensions.

```

Nothing on the "lsmod"

---

### Post by Bachstelze on 2008-03-21
All right, do this :

```
sudo modprobe ipw2200
```

If it just says nothing, do *iwconfig* again and see if the wireless interface appeared.

---

### Post by kanatejr on 2008-03-21
```
FATAL: Error inserting ipw2200 (/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg) 
```

---

### Post by kanatejr on 2008-03-24
*Bump*

Please help!

---

### Post by Whiffle on 2008-03-24
After you do the sudo modprobe, what does "dmesg" say, should be something useful in the last 10-20 lines or so.

---

### Post by kanatejr on 2008-03-25
sudo modprobe ipw 2200 came up with the FATAL line...

sudo modprobe gives out nthng useful, likedefine parameters and modnames only...

Loaded from LiveCD and it supports out of the box, both wired and wireless... How do I get this to work in normal mode tho?

---

### Post by kanatejr on 2008-03-25
Seems like Ubuntu 7.10 does not detect LAN and wireless, tried entering all possible dhcp/static ip from xp. Hope avails.

Will reinstalling help since they were detected with LiveCD

---

### Post by kanatejr on 2008-03-26
Everything now works. Seems like the LiveCD was faulty. Thanks for all the help!

---

