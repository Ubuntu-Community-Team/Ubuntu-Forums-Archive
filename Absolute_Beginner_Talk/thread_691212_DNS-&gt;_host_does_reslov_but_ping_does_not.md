---
title: "DNS-&gt; host does reslov but ping does not"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by byenary on 2008-02-08
Hello,

I have set up a DNS server gutsy 7.10 with bind9, with my fixed ip all is fine, dhcp clients are not resolving, dns address 192.168.123.10 is assigned by the router and when i have al ook on a ubuntu dhcp client in his resolv.conf 192.168.123.10 is present.
When i do ->host router.test.local it is resolving is ip adress and says it is 192.168.123.1
when i do ->ping router.test.local, it says unknown host... ????

Anybody ?
Thx

---

### Post by bumanie on 2008-02-08
Ithink you may have the ipv6 problem that a number of users have faced under gutsy.
There are two ways to fix this, both of which are reversible if they don't work.
Method1.
> gksudo gedit /etc/modprobe.d/blacklist
at the end of the gedit list type
> blacklist ipv6. 
Save and reboot. 

Method 2.
Type > about:config in your firefox address bar
Type "ipv6" in the filter 
Change the value of "network.dns.disableIPv6" to true

---

### Post by byenary on 2008-02-14
This was no solution for me, can't do method 2 since it has no gui., others ?

---

### Post by hyper_ch on 2008-02-14
pls post the output of:

```

cat /etc/network/interfaces

```

```

cat /etc/hosts

```

```

cat /etc/hostname

```

```

cat /etc/resolv.conf

```

---

