---
title: "how to load kernel modules in a specific order"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by AntoC on 2008-04-04
Hi everyone,
when booting my box I get an error that says the driver 8139c is not good , trying the 8139too ok
What I would like todo is to make my distro load the right kernel module for my ethrnet, basically I would like to swap the order in which those two modules are loaded, does anyone know how to achieve this?

Thanks in advance,
Antonio

---

### Post by Oldsoldier2003 on 2008-04-04
> **AntoC said:**
> Hi everyone,
when booting my box I get an error that says the driver 8139c is not good , trying the 8139too ok
What I would like todo is to make my distro load the right kernel module for my ethrnet, basically I would like to swap the order in which those two modules are loaded, does anyone know how to achieve this?

Thanks in advance,
Antonio

have you tried editing /etc/modules ?

---

### Post by mtbeedee on 2008-04-04
I believe you need to edit /etc/modules.

You might then also need to edit /etc/modprobe.d/blacklist to add the modules... I am not sure about this part.

---

### Post by AntoC on 2008-04-04
Hi guys thank you for answering...

I have black listed the mod 8139cp and the result is still:
```

[   11.772355] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.808000] 8139cp 0000:06:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    2.808000] 8139cp 0000:06:01.0: Try the "8139too" driver instead.
[    2.808000] 8139too Fast Ethernet driver 0.9.28
[    2.808000] eth0: RealTek RTL8139 at 0xf884e000, 00:0f:b0:8f:db:fe, IRQ 21
[    2.808000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'

```

Any ideas on how to load 8139too on boot?

---

### Post by herbster on 2008-04-04
Add 8139too to /etc/modules?

---

### Post by AntoC on 2008-04-04
that way,It doesn't load at startup, it should but it doesn't

---

### Post by AntoC on 2008-04-05
Any ideas?

---

### Post by saltydog on 2008-04-26
I've got the same problem and now my server is stuck. No way to let the system loads only the 8139too driver.

---

