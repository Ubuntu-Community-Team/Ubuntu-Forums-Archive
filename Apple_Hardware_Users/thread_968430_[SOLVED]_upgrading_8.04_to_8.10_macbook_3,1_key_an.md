---
title: "[SOLVED] upgrading 8.04 to 8.10 macbook 3,1 key and wifi problems."
date: 2008-11-02
forum: Apple Hardware Users
---

### Post by mkgkg on 2008-11-02
hi, i 've upgraded from 8.04 to 8.10 .
two main issues:

-before i was using ndiswrapper driver but now doesn t work so i removed it by apt-get remove ndiswrapper-utils-1.9 and i used the broadcom driver installed from System>administration>hardware drivers and then active.every time i reboot wifi didn't work, i have always to do System>administration>hardware drivers and disactive broadcom and the activated..any idea?

-one of the two brightness key didn't work(F2 key,upper brightness), and the eject -key.
i removed pommed but it 's still the same problem.any idea?i set up a normal keyboard with 105 characters.

---

### Post by hanzomon4 on 2008-11-02
macbook pro 3.1 sure you don't have an atheros card. That's what I have in my 3.1 macbook pro.

---

### Post by mkgkg on 2008-11-03
no..i don 't have it.
i have this one:
- 02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

the broadcom driver works well, the problem is that every boot not start automatically and so i have to do System>Administration>hardware detection and deactive broadcom driver and then reactive and reinstall and only after this operation wifi works .

---

### Post by cyberdork33 on 2008-11-03
> **hanzomon4 said:**
> macbook pro 3.1 sure you don't have an atheros card. That's what I have in my 3.1 macbook pro.
He has a MacBook, not a MacBook Pro.

> **mkgkg said:**
> no..i don 't have it.
i have this one:
- 02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

the broadcom driver works well, the problem is that every boot not start automatically and so i have to do System>Administration>hardware detection and deactive broadcom driver and then reactive and reinstall and only after this operation wifi works .
I assume you are enabling the Broadcom _STA_ driver? If so you need to make sure to blacklist b43 and ssb so they do not conflict on startup. You can add these two modules to /etc/modprobe.d/blacklist

---

### Post by mkgkg on 2008-11-03
i resolved any problem of upgrading by reinstalling ubuntu 8.10 .now everything works:)

---

