---
title: "Kubuntu 6.10 Network problems"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by alexius on 2006-12-27
Hi all. I am brand new at Linux. 20 years of MS and now this! :confused: 
I have installed Kubuntu 6.10 - everything went well - except I have no network details at all and I can not add anything to get my network up and running. As a result I have no internet connectio either. When I go to network connections I have nothing in Network interfaces, If I try (as adminstrator) to add anything to routes - it will not allow me to do so. No devices are available.In domain name systems I have:-
IP Address  Aliases
::1             ip6-localhost ip6-loopback
127.0.0.1   localhost
127.0.0.1   family-pc
fe00::0      ip6-localnet
ff00::1       ip6-mcastprefix
ff02::1       ip6-allnodes
ff02::2       ip6-allrouters
ff02::3       ip6-allhosts

Network profiles is empty

My system has a NE2000 compatible ISAPNP Etnernet adapter connected to a D-Link DI-624 wireless router connected to a D-link ADSL modem DSL-300T.

Any suggestions where to now?

Alex

---

### Post by MrHorus on 2006-12-27
> **alexius said:**
> 
Any suggestions where to now?

Alex

```
sudo dhclient
```

Please post the output.

---

### Post by alexius on 2006-12-27
I get the following:

No broadcast interfaces found - exiting

Now what? Please can some one help - I need to get my system working.

Regards

Alex

---

### Post by alexius on 2006-12-31
Can anyone advise me what to do next?
Should I uninstall 6.10 and go back to 6.06? If so how do I do that?
I cannot understand why I cannot find my network or my internet connection?
Regards
Alex

---

