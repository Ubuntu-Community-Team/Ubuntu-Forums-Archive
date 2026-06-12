---
title: "WPA on Macbook 4.1"
date: 2008-09-28
forum: Apple Hardware Users
---

### Post by johnlocke2342 on 2008-09-28
Hi.
I've got a MacBook 4.1 (current model) on which I installed Ubuntu Hardy.
Everything works fine, but connecting to a WPA-protected wifi network is impossible.
Could anyone tell me how to do?

---

### Post by hajk on 2008-09-28
Yes, check out the new Broadcom wl.ko driver, see the sticky at the top of the Networking sub-forum. There are also a couple of recent threads on it in the Apple sub-forum.

Several users have reported that WPA/WPA2 Personal doesn't work in combination with Ndiswrapper and the Windows driver for the Broadcom 4328 rev 05 wireless chip in the MBP 4,1. Those same users have also reported that the new Broadcom wl.ko driver does work with WPA/WPA2 Personal security.

---

### Post by johnlocke2342 on 2008-10-02
Yep, I tried it ... and it failed!

---

### Post by cyberdork33 on 2008-10-02
> **johnlocke2342 said:**
> Yep, I tried it ... and it failed!
Can you be more specific? It is hard to determine your problem when you do not describe the problem clearly. Does the interface show up still? Are you getting an IP? Are you using network-manager? Have you tried wicd?

---

### Post by johnlocke2342 on 2008-10-02
Sorry.
I tried wicd, it never worked.
The interface still shows up. I'm not getting an IP, that's why I reverted back to original settings and to WEP protection.

---

### Post by cyberdork33 on 2008-10-02
> **johnlocke2342 said:**
> Sorry.
I tried wicd, it never worked.
The interface still shows up. I'm not getting an IP, that's why I reverted back to original settings and to WEP protection.
I lot of people have been having similar issues recently... Just for fun, have you tried setting an IP manually? maybe tried a different dhcp client?

---

### Post by jamsaver on 2008-10-02
I am also using macbookpro 4.1, and having the same problem with wpa on wl driver...
anyone know the magic solution for this??

---

