---
title: "Mac Address changing..."
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2006-08-26
Hi!
Does anyone know how? Thanx in advance!

---

### Post by OffHand on 2006-08-26
> **the_nomad said:**
> Hi!
Does anyone know how? Thanx in advance!

Mac address of what?

---

### Post by the_nomad on 2006-08-26
you know... network address ](*,)

---

### Post by annda on 2006-08-26
i don't know exactly what you are trying to do, but maybe take a look here:
[http://en.wikipedia.org/wiki/MAC_address#Linux](http://en.wikipedia.org/wiki/MAC_address#Linux)

---

### Post by Woei on 2006-08-26
> **the_nomad said:**
> Hi!
Does anyone know how? Thanx in advance!

ifconfig eth0 hw ether aa:bb:cc:dd:ee:ff.

If you want to change the MAC address permanently, either flash your NICs ROM with a utility provided by the card's manufacterer, or change your /etc/network/interfaces file. The stanza you're interested in reading up on is 'hwaddress ether'. Check 'man 5 interfaces' on a terminal.

---

### Post by the_nomad on 2006-08-26
10x alot! and how do i set it back to default? manually?

---

### Post by Woei on 2006-08-26
> **the_nomad said:**
> 10x alot! and how do i set it back to default? manually?

Unless you flash the ROM on the NIC, the MAC address will revert to the factory default after a reboot when doing it manually through ifconfig eth0 hw ether, or after you remove the hwaddress stanza from /etc/network/interfaces and reboot.

---

