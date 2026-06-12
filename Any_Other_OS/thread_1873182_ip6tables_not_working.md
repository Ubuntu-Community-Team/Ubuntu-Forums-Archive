---
title: "ip6tables not working"
date: 2011-10-31
forum: Any Other OS
---

### Post by jeff.sadowski on 2011-10-31
I'm using Linux Mint version 10
uname -a
displays
Linux jeff-server.sadowski.home 2.6.35-30-generic #59-Ubuntu SMP Tue Aug 30 19:00:03 UTC 2011 x86_64 GNU/Linux

I setup ipv6 through Hurricane Electric.
I have it working good but I tried locking it down as follows

ip6tables -A INPUT -s ::1 -j ACCEPT
ip6tables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
ip6tables -A INPUT -s :: -j DROP

Similar to my ipv4 tables that work.

But when I go to hurricane electric's port detector it still sees all my open ports when I give it the ipv6 address on my eth1 interface.
How do I block ipv6 traffic?

Do I need to load a kernel module or something?

---

### Post by Dangertux on 2011-11-01
Some kernels are not compiled with netfilter 6 conntrack state matching by default.

You need to make sure your kernel is compiled with options CONFIG_NETFILTER_XTABLES and CONFIG_NETFILTER_XT_MATCH_STATE

hope this helps.

---

### Post by jeff.sadowski on 2011-11-01
> **Dangertux said:**
> Some kernels are not compiled with netfilter 6 conntrack state matching by default.

You need to make sure your kernel is compiled with options CONFIG_NETFILTER_XTABLES and CONFIG_NETFILTER_XT_MATCH_STATE

hope this helps.

So the default kernels by Ubuntu won't filter ipv6 traffic?

You can't compile or load them as modules?

Thanks I'll look for those options and probably recompile my kernel.

---

### Post by Dangertux on 2011-11-01
conntrack state matching has always been iffy with ip6tables. Check the netfilter.org mailing list before recompiling obviously, but that is the only fix I've ever gotten to work. 

 Hope that helps.

---

### Post by Perfect Storm on 2011-11-01
Moved to Other OS/Distro Talk.

---

### Post by jeff.sadowski on 2011-11-06
It turns out that the kernel did support it. my problem was how I was trying to represent any.

What was failing was

ip6tables -A INPUT -s :: -j DROP

doing this instead fixed my issues

ip6tables -P INPUT DROP

my start up script look as follows

. /etc/interfaces
for ip in `grep -v -e "^;" -e "^$" /etc/whitelist.ipv6`;do
 /usr/sbin/scripts/ipv6allow.sh $ip;
done
ip6tables -A INPUT -s ::1 -j ACCEPT
ip6tables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
ip6tables -A INPUT -i ${INSIDE} -p icmpv6 -j ACCEPT
ip6tables -A INPUT -p udp --dport 53 -j ACCEPT
ip6tables -P INPUT DROP
ip6tables -A OUTPUT -p icmpv6 -j ACCEPT
ip6tables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
ip6tables -A OUTPUT -p udp --dport 53 -j ACCEPT
ip6tables -P OUTPUT DROP
ip6tables -A FORWARD -i ${INSIDE} -p icmpv6 -j ACCEPT
ip6tables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
ip6tables -A FORWARD -p udp --dport 53 -j ACCEPT
ip6tables -P FORWARD DROP


/usr/sbin/scripts/ipv6allow.sh looks like

#!/bin/bash
ip6tables -I OUTPUT 1 -s $1 -j ACCEPT
ip6tables -I FORWARD 1 -s $1 -j ACCEPT
ip6tables -I INPUT 1 -s $1 -j ACCEPT

/etc/whitelist.ipv6 has an entry for my ipv6 scope from hurricane electric

and /etc/interfaces looks as follows

export OUTSIDE=`ifconfig -a | grep <mac of my outside port>|cut -d" " -f1`
export INSIDE=`ifconfig -a | grep <mac of my inside port>|cut -d" " -f1`

Maybe my documentation will help others.

---

### Post by Dangertux on 2011-11-06
Sweet. Glad you figured it out.

---

