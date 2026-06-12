---
title: "I cannot connect to Ubuntu on vmWare"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Davide_CH on 2007-06-07
Hi, I'm totally new to Ubuntu so excuse me if I ask some really really basic questions.

I have windows xp and vmware Workstation. I've installed ubuntu Feisty on vmware.

The first problem I see is that I CAN ping from windows to ubuntu without a problem. but I CAN'T ping from ubuntu to windows. That is

ping 192.168.1.3 (this is the ubuntu IP address on vmWareWorkstation)  (from windows) OK

ping 192.168.1.2 (windows static IP address) from ubuntu, NOTHING in response, packets lost

I really don't know what I have to do because I'm not an expert of net configuring.

Thanks in advance for any suggestion.

Davide

---

### Post by sandwitch on 2007-06-07
maybe this is not ubuntu related but vmware. Have set up nat ethernet or bridged?  for pinging the host it should be bridged i guess (pardon me if i'm wrong)

---

### Post by Davide_CH on 2007-06-07
Yes, the wmware is in bridged mode

---

### Post by sandwitch on 2007-06-08
if your network is realy up there should be a route database. Run "route -n" to check this

---

