---
title: "Contiki OS network stack confusion"
date: 2013-03-05
forum: Any Other OS
---

### Post by flldom001 on 2013-03-05
Hi, 

the Contiki mailing list is down and I was hoping there was somebody here that I could ask for help with regards to their confusing network/communication stack:

[FONT=arial]I note that in contiki-z1-main.c , **set_rime_addr()** is used to help set the ipv6 address of the sensor mote. But the rime stack is not used as is indicated by **NETSTACK_CONF_NETWORK = sicslopan** in contiki_conf.h. Is this correct? Rime is only used here to set the IP address?[/FONT][FONT=arial]
[/FONT]
[FONT=arial]I also note that in contiki-z1-main.c, when **WITH_UIP6 =1** (i.e. we are using the IPv6 version of uIP), X-MAC is the MAC layer that is set up, however in contiki_conf.h it says **NETSTACK_CONF_MAC = csma_driver**, is this X-MAC? [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Also the Radio duty cycling (**RDC**) is set to **contiki_mac driver**... I can't quite figure out where this fits in with X-MAC, or is X-MAC the superset of **csma_driver** & **contiki_mac**?[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Contiki really needs a clear taxonomy to be defined for it operating/network stacks.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Your help us greatly appreciated.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Regards[/FONT]

---

