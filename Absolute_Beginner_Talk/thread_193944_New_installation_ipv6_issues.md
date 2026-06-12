---
title: "New installation: ipv6 issues"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by ktorn on 2006-06-10
Hi all,

I just installed the latest version of Ubuntu.

The installation was great. Without a doubt the best OS installation I've ever come across.

But a slight issue with my networking... I'm using a netgear PCMICA wifi card, and after setting the right WEP name and key, it seems to connect to the AP, but still can't browse anywhere using the default web browser.

So I typed 'ifconfig' and it's showing an IPV6 address for that card, but no IPV4. I don't even know how to ping my router (which uses IPV4).

How to I make it use IPV4?

---

### Post by manicka on 2006-06-10
by the default browser I assume you mean firefox

in the address bar type

*about:config*

in the filter field type

*ipv6*

then toggle **networkdns.disableIPv6** to **true**

---

### Post by ktorn on 2006-06-10
I did just that, but still nothing.

I think my problem is with the actual system's network configuration. I went to the Network settings and the Wireless connection only shows an ipv6 address.

Same thing when I opened a terminal window and typed 'ifconfig'. Shows an ipv6 address for the wireless connection. The only ipv4 address is the local loop (127.0.0.1).

I don't use ipv6 at all. Is there a way to switch it off and use ipv4?

---

### Post by Jagot on 2006-06-10
[https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4)

---

### Post by ktorn on 2006-06-10
Thanks Jagot.

My actual problem was a wrong WEP key, but strangely enough the lights on the wifi card led me to believe it was connecting correctly. The ipv6 ip address also threw me off in the wrong path.

Anyway, it works now and I have disabled ipv6 anyway (since I'm not using it) by following the URL you posted.

Once again thanks!

---

