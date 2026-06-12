---
title: "PCMCIA file missing"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by RockDog on 2006-06-26
I am trying to set up an iBurst modem on a server installation (Dapper Drake) and following the howto as posted. I cannot find the following file /etc/default/pcmcia.
What is the difference between the pcmcia file and pcmciautils found in /etc/init.d

---

### Post by hw-tph on 2006-06-26
The file /etc/init.d/pcmcia is used by the pcmcia-cs package. For kernels later than 2.6.13-rc1 pcmciautils is used instead, and this has its own init script, /etc/init.d/pcmciautils.

Here is the default /etc/default/pcmcia as found on my system. Note that this is only used by the pcmcia-cs package; pcmciautils uses /etc/default/pcmciautils instead.

```
# Defaults for PCMCIA (sourced by /etc/init.d/pcmcia)
PCMCIA=yes
PCIC=i82365
PCIC_OPTS=
CORE_OPTS=
CARDMGR_OPTS=
# If REFRAIN_FROM_IFUP is set to yes, cardmgr will not bring up
# network interfaces. They should be brought up by hotplug instead.
REFRAIN_FROM_IFUP=yes
```

i82365 is the most common PCIC so it should work OK, otherwise change as needed (yenta is the other common PCIC, if I recall correctly).


Håkan

---

