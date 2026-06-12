---
title: "Slow internet connection"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by bachibusuc on 2007-12-12
Hi,

I recently installed ubuntu(kubuntu as well) and im a n00b. My internet connection is very slow. I d like to know if i have to install a driver for my network card and if yes, where do I look to see what's my network card. I've read at some places it might be because of a DNS or something... Anyways if anyone could help me, that'd be nice!

---

### Post by skymera on 2007-12-12
my ubuntu internet was dead slow when i installed.

i done countless mods and they worked.

disable IPv6 mainly.

also switch dns, 

[www.opendns.com](www.opendns.com)

a simple google search reaps mountains of answers, good luck with the speed :)

---

### Post by Johnny3 on 2007-12-12
Try about:config in address bar of Foxfire and  look for network.dns.disableIPv6 and set to true. If you are in USA.
Johnny3

---

### Post by skymera on 2007-12-12
also enable pipelining and fiddl;e with the settings.

maxrequests=30 etc just notch them up

---

### Post by bachibusuc on 2007-12-12
Thank you for the prompt response,

the thing is that I have absolutely no Idead of what you guys are talking about (DNS or ipv6 or something like that...)

I d search on google, but internet is so slow, it takes me about 5 minutes to write this message...

Thanx!

---

### Post by skymera on 2007-12-12
o damn, ifind some styuff, copy and paste for you, hold tight, 5mins bud.

---

### Post by t0p on 2007-12-12
Ok dude... as Johnny3 said above, type
```
about:config
```
into the address bar of Firefox.  This will call up a list of stuff that you can configure. Look for 
```
network.dns.disableipv6
```
and click on it.

---

### Post by skymera on 2007-12-12
```

sudo gedit /etc/modporbe.d/aliases
 
    add to end:


alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6

```

```

1. Open a terminal window and type the following.

    $ sudo network-admin

Note: Root access is required for this step.
2. Change to the DNS tab and enter the following two addresses in the top of the first field labeled DNS Servers.

    208.67.222.222
    208.67.220.220

To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ sudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

```

```

sudo gedit /etc/sysctl.conf

ADD TO THE END

net.core.rmem_max = 524288

net.core.wmem_default = 524288

net.core.wmem_max = 524288

net.ipv4.tcp_wmem = 4096 87380 524288

net.ipv4.tcp_rmem = 4096 87380 524288

net.ipv4.tcp_mem = 524288 524288 524288

net.ipv4.tcp_rfc1337 = 1

net.ipv4.ip_no_pmtu_disc = 0net.ipv4.tcp_sack = 1

net.ipv4.tcp_fack = 1net.ipv4.tcp_window_scaling = 1

net.ipv4.tcp_timestamps = 1net.ipv4.tcp_ecn = 0

net.ipv4.route.flush = 1

THEN

sudo sysctl -p


```

those should mainly help, tghe last one did for me, quite a lot.

---

### Post by bachibusuc on 2007-12-12
hey,

well i did evertyhing u guys said and still slow.... i changed everything, but oh well. I ll come back later for explanations :) ... i ll read a little bit about linux first I guess... 

thank you so much tho

---

### Post by skymera on 2007-12-12
no problem.

what is your itnernet connection speed?

type?
-wireless
-wired
-usb wireless
-pci wireless etc

---

### Post by t0p on 2007-12-12
Oh I forgot to mention: if you use Firefox, there's an add-on available called Fasterfox.  It helps to configure the browser for maximum speed, and it can also enable a feature called "enhanced prefetching" that some people say really speeds things up.  Though YYMV, enhanced prefetching does nothing for me.

---

### Post by starryeyedboy on 2007-12-14
Fasterfox worked for me - my surfing speed in firefox is at least as fast as in windows now.

for your convenience:
[https://addons.mozilla.org/en-US/firefox/addon/1269](https://addons.mozilla.org/en-US/firefox/addon/1269)

Cheers.

---

