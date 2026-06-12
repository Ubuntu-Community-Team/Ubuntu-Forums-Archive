---
title: "how to configure two networks on ubuntu"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Guruprasad on 2008-01-30
I installed ubuntu on a computer with two network cards.

one card is for internet with dhcp. this one got configured and works fine.

the other card is for local intranet which should have ip 192.168.100.101. this is not working

can anyone help me in configuring the other card?

---

### Post by mikeyphi on 2008-01-30
> **Guruprasad said:**
> I installed ubuntu on a computer with two network cards.

one card is for internet with dhcp. this one got configured and works fine.

the other card is for local intranet which should have ip 192.168.100.101. this is not working

can anyone help me in configuring the other card?

Open Network Manager - highlight local card - select properties....enter required data under static address click OK
Under General tab - enter Domain name
Also set 
DNS server and search domains under DNS - if not there

Probably need to reboot to take effect.

---

